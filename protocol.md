English:
OpenMind: Hardware Abstraction Layer (HAL) Protocol

Objective: Standardizing commands for humanoid robots to perform domestic tasks in unstructured environments.

1. Manipulation Standard (Arms/Hands)
The robot MUST support Cartesian Space Control for end-effectors.
Command: move_to(target_coordinates, velocity, force_limit)
Grasp Event: grasp_object(rigidity_factor) — The low-level controller autonomously determines grip force based on object rigidity (e.g., egg vs. frying pan).

2. Visual Feedback (Vision)
OpenMind utilizes cloud-based object recognition. The hardware MUST stream:
Data Stream: Point Cloud or RGB-D frames.
Frequency: Minimum 30 FPS for dynamic tasks (e.g., flipping bacon).

3. Experience Telemetry (The Experience Log)
After each session, the robot MUST generate an experience.json file for the cloud brain:
success_rate: Float (0.0 – 1.0) based on user feedback.
force_profile: Time-series data of grip and contact forces.
error_log: Diagnostic data on failure points (slippage, joint overheat, collision).

4. Safety Constraints (Kill-Switch)
All OpenMind commands MUST pass through a local hardware safety filter:
Velocity Limit: Immediate halt if human contact is detected at speeds > 0.5 m/s.
Thermal Safety: Blocking contact with surfaces > 60°C without specialized end-effectors.




Russian:
protocol.md (OpenMind Hardware Abstraction Layer)

Цель: Унификация команд для любого гуманоидного робота при выполнении бытовых задач.

1. Стандарт манипуляции (Arms/Hands)
Робот должен поддерживать векторное управление в пространстве (Cartesian Control).
Команда: move_to(target_coordinates, velocity, force_limit)
Событие захвата: grasp_object(rigidity_factor) — робот сам определяет силу сжатия на основе жесткости объекта (яйцо vs сковорода).

2. Визуальный фидбек (Vision)
OpenMind использует облачное распознавание объектов. Робот передает:
Поток данных: Point Cloud (облако точек) или RGB-D кадры.
Частота: Минимум 30 FPS для динамических задач (жарка).

3. Телеметрия опыта (The Experience Log)
После каждой сессии робот генерирует файл experience.json:
success_rate: 0.0 – 1.0 (оценка пользователя).
force_profile: График усилий при разбивании яйца.
error_log: Почему не получилось (проскальзывание, перегрев).

4. Безопасность (Kill-Switch)
Любая команда от OpenMind должна проходить через локальный фильтр безопасности робота:
Запрет на контакт с человеком на скорости > 0.5 м/с.
Контроль температуры поверхности (не брать горячее голыми руками без перчаток).
