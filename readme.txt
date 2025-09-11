📘 Tsetlin GUI User Guide

1. Installation
    1. Run MyAppInstaller_web.exe
       - If Windows shows “Windows protected your PC” → click More info → Run anyway
    2. Choose an installation folder (e.g., 'C:\Program Files\TsetlinGUI') and click Next / Install
    3. The installer will install TsetlinGUI.exe and create a shortcut on the Desktop or Start Menu
    4. MATLAB Runtime
       - If your system does not have the required MATLAB Runtime, the installer will download and install it automatically
    5. Once installed, double-click TsetlinGUI.exe to start the program

2. Preparing Data
    - Download or locate TsetlinGUI.exe (from the installation step above)
    - Prepare datasets for Training and optionally for Testing
    - Data must be in .csv format, with features in each column and the label in the last column

    Example:
    0,1,0,1
    1,0,1,0
    (Each row is one sample)

3. Opening the Program
    Double-click TsetlinGUI.exe → The GUI window will appear with buttons and parameter fields

4. GUI Components
    🔹 File Selection
        - Training File: Select dataset for training
        - Test File (optional): Select dataset for testing. If not selected, only the training set will be used

    🔹 Main Parameters
        - Threshold (T) – Controls decision threshold
        - Sensitivity (s) – Controls adjustment sensitivity
        - Number of Clauses – Number of clauses used
        - Number of States – Resolution of the state machine
        - Number of Epochs – Number of training iterations

        💡 Number of Classes: Not user-defined. The program automatically detects the number of classes from the training file (last column labels).

    🔹 Sweep Mode
        - Test multiple values automatically (e.g., Threshold 10 → 100 with step size 10)
        - SweepTarget: Choose which parameter to sweep (Threshold / Sensitivity)
        - SweepOrder: Define order when sweeping multiple parameters
        - Step / To: Define starting value, step size, and end value

    🔹 Control Buttons
        - Train – Start training
        - Stop – Stop training
        - Reset – Reset all parameters
        - Lamp Indicator – Shows status (Green = success, Orange = error/warning)

5. Basic Usage
    1. Click Select Training File and choose a .csv file
    2. Optionally select a Test File
    3. Set parameters (e.g., Threshold = 15, Sensitivity = 3.9)
    4. Click Train
    5. GUI will display accuracy results and a learning curve graph

6. Sweep Mode
    To find the best parameter values:
        1. Select Sweep Mode
        2. Configure ThresholdStep and/or SensitivityStep
        3. Choose whether to sweep one parameter or both (via SweepOrder)
        4. Click Train
        5. GUI will iterate through the defined ranges and display the best results

7. Results
    - Displays Training Accuracy and Test Accuracy
    - Shows Accuracy Curve (Learning Curve)
    - Use results to select the best parameters

8. History Button
    Opens the Training History window, which records all past training sessions.

    Displayed Information:
        - Timestamp – Date and time of training
        - Mode – Fix (fixed values) or Sweep (parameter sweeping)
        - SweepTarget / SweepOrder – Which parameters were swept and in what order
        - Threshold / Sensitivity (Start, End, Step) – Parameter ranges used

    Control Buttons:
        - Open Folder – Open result folder (e.g., history\results.xlsx)
        - Refresh – Reload the latest history
        - Clear All – Delete all history records

    Saved Results:
        - Automatically saved in an Excel file (results.xlsx)
        - Can be opened in Excel for further analysis

9. Notes
    - If no Test File is selected, the program will warn but still allow training
    - The .csv file must not contain a header row (e.g., X1, X2, Y)
    - The label must always be in the last column
    - Number of classes is automatically detected from the training file
