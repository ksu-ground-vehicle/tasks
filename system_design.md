# Design of the GV
## Software
### Nodes
1. orb_slam2
    1. Inputs: camera data
    2. Outputs: Gives current position
2. gps_arduino
    1. Inputs: gps sensor
    2. Outputs: broadcasts GPS location samples in ros
        1. average multiple samples and periodically broadcast to ros
        2. GPS -> arduino -> ros
3. lidar
    1. Inputs: lidar sensor
    2. Outputs: 360 laser-scan
        1. Gives laser scan data
    3. Future: Nearby obstacle tracking?
        1. Perhaps use with mapping program
4. line_detector
    1. Inputs: Camera data
    2. Outputs: location of grid lines
5. path_planner
    1. Inputs: takes in orbslam data, lines, gps, lidar
    2. Outputs: a path through obstacles
6. pid_controller
    1. Inputs: path from path_planner
    2. Outputs: pwm values to arduino
    3. Sends ints for pids to the arduino
        1. current_location, path -> pid_controller -> arduino -> motor controller
