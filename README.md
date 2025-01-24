# Huawei Storage Script Generator

This Python application generates scripts for Huawei Storage Cabinets based on user input provided via Excel files and a JSON configuration. The application dynamically adapts to changes in the JSON file, making it highly customizable and scalable.

## Features

- **Dynamic Configuration**: The application reads from a JSON file to determine the available resource types (e.g., CIFS, NFS, FileSystem) and their associated commands (e.g., Create, Change, Show).
- **Excel-Based Input**: Users can input data via Excel files, which are automatically generated by the application.
- **User-Friendly GUI**: The application provides a graphical user interface (GUI) for easy interaction.
- **Executable Packaging**: The application can be packaged into an executable (.exe) file for easy distribution.

## Getting Started

### Prerequisites

- Python 3.x
- Required Python packages (install via pip):

  ```bash
  pip install pandas openpyxl tkinter

# Running the Application

## Clone the Repository:

```bash
git clone https://github.com/javimcasas/huawei-storage-script-generator.git
cd huawei-storage-script-generator
```

# Application Guide

## Launch the Application:
Run the `script_selector.py` script to start the application:

```bash
python script_selector.py
```

## Using the Application:
1. Select a resource type (e.g., CIFS, NFS, FileSystem) from the dropdown menu.
2. Choose a command type (e.g., Create, Change, Show).
3. Click **Open Excel** to generate and open an Excel file for data input.
4. Fill out the Excel file with the required data.
5. Click **Run Script** to generate the commands. The output will be saved in the `Results` folder.

## JSON Configuration
The application dynamically adapts to changes in the `commands_config.json` file. This file defines:

- The available resource types (e.g., CIFS, NFS, FileSystem).
- The commands associated with each resource type (e.g., Create, Change, Show).
- The mandatory and optional fields for each command.

### Example JSON structure:
```json
{
    "CIFS": {
        "Create": {
            "mandatory": [
                {
                    "name": "name",
                    "field_type": "text"
                },
                {
                    "name": "local_path",
                    "field_type": "text"
                }
            ],
            "optional": [
                {
                    "name": "oplock_enabled",
                    "field_type": "select",
                    "allowed_values": ["yes", "no"],
                    "default": "yes"
                }
            ]
        }
    }
}
```

## Packaging the Application
To create an executable (.exe) file, use the `exe_creator.py` script. This script packages the application and its dependencies into a single executable file.

### Install PyInstaller:
```bash
pip install pyinstaller
```

### Create the Executable:
Run the `exe_creator.py` script:

```bash
python exe_creator.py
```

The executable will be created in the `dist` folder.

## File Structure
```
huawei-storage-script-generator/
├── script_selector.py          # Main application script
├── exe_creator.py              # Script to create an executable
├── commands_config.json        # JSON configuration file
├── Documents/                  # Folder for generated Excel files
├── Results/                    # Folder for generated script files
├── README.md                   # Project documentation
└── requirements.txt            # List of required Python packages
```

## Contributing
Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Example Usage

### Launch the Application:
```bash
python script_selector.py
```

### Generate Commands:
1. Select a resource type (e.g., CIFS).
2. Choose a command type (e.g., Create).
3. Fill out the Excel file and click **Run Script**.

### View Output:
The generated commands will be saved in the `Results` folder (e.g., `cifs_commands.txt`).
