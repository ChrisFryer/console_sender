# Universal Text Sender (Originally for VMware Console)

A PowerShell utility for sending text commands to any active window, originally designed for VMware console windows but compatible with any application that accepts keyboard input.

## Overview

This script automates the process of sending text to any active application window by using Windows Forms SendKeys functionality. While originally created for VMware console environments where copy-paste might not work reliably, it can be used with any application including terminal emulators, remote desktop sessions, virtual machines, or any text input field.

## Features

- **Universal Compatibility**: Works with any Windows application that accepts keyboard input
- **Timed Execution**: 5-second countdown gives you time to switch to the correct window
- **Interactive Setup**: Clear instructions and key press confirmations
- **Flexible Input**: Easily customise the command/text to be sent
- **Error Prevention**: Built-in prompts to ensure proper setup before execution

## Prerequisites

- Windows PowerShell 5.1 or PowerShell 7+
- Any Windows application that accepts keyboard input (VMware consoles, terminal emulators, remote desktop, etc.)
- Appropriate permissions in the target application/system if needed

## Usage

### Basic Setup

1. **Edit the Script**: Open `send-text-VMware-console.ps1` and modify the `$command` variable:
   ```powershell
   $command = @"
   Your command or text here
   Multiple lines supported
   "@
   ```

2. **Prepare Your Target Application**:
   - Open your target application (VMware console, terminal, remote desktop, etc.)
   - Navigate to the appropriate command prompt or text input area
   - Ensure you have the necessary permissions for your command

3. **Run the Script**:
   ```powershell
   .\send-text-VMware-console.ps1
   ```

### Step-by-Step Execution

1. **Launch**: Run the PowerShell script
2. **Read Instructions**: The script displays setup instructions in color-coded text
3. **Prepare Target Window**: Click on your target application window to make it active
4. **Confirm Ready**: Press any key in the PowerShell window to start the countdown
5. **Switch Windows**: Quickly switch back to your target application during the 5-second countdown
6. **Automatic Execution**: The script sends your text and presses Enter

## Common Use Cases

### VMware and Virtualization
- **VM Configuration**: Sending long configuration snippets to virtual machines
- **Installation Scripts**: Automating installation commands in VMs
- **Network Configuration**: Inputting complex network settings

### Terminal and Command Line
- **SSH Sessions**: Sending commands to remote servers via SSH clients
- **PowerShell/CMD**: Automating command sequences in local terminals
- **Linux Terminals**: Sending bash scripts or configuration to WSL or remote systems

### Remote Desktop and Applications
- **RDP Sessions**: Inputting text into remote desktop applications
- **Legacy Applications**: Working with older applications with limited clipboard support
- **Text Editors**: Quickly inserting large blocks of text or code

### General Automation
- **Form Filling**: Automating repetitive data entry tasks
- **Configuration Management**: Sending configuration files to various applications
- **Troubleshooting**: Sending diagnostic commands when clipboard access is limited

## Important Notes

### Security Considerations
- **Review Commands**: Always verify the content of `$command` before execution
- **Privileged Access**: Be cautious when running commands with elevated privileges
- **Sensitive Data**: Avoid including passwords or sensitive information in the script

### Timing Considerations
- **Window Focus**: Ensure the target application is the active window when the countdown reaches zero
- **Input Speed**: The script sends text immediately; ensure the target system can handle the input speed
- **Ready State**: Make sure the application is ready to accept input (proper prompt displayed, cursor in text field, etc.)

### Compatibility
- **Applications**: Works with any Windows application that accepts keyboard input
- **VMware Products**: Originally designed for and tested with VMware Workstation and vSphere Client  
- **Terminal Emulators**: Compatible with PuTTY, Windows Terminal, PowerShell, Command Prompt, etc.
- **Remote Applications**: Works with RDP, VNC, and other remote access tools
- **Target Systems**: Compatible with any system that the host application connects to

## Troubleshooting

**Script doesn't send text:**
- Verify target application window is active and focused
- Check that the cursor is in the correct input area (text field, command prompt, etc.)
- Ensure PowerShell execution policy allows script execution

**Text appears garbled or incomplete:**
- The target application might be processing input too slowly
- Try breaking long commands into smaller chunks
- Verify the target system's keyboard layout matches your input
- Some applications may have input rate limits

**Permission errors:**
- Run PowerShell as Administrator if needed
- Verify you have appropriate permissions in the target application/system
- Some applications may block programmatic keyboard input for security reasons

### Customisation

### Modifying the Countdown Timer
Change the countdown duration by modifying the for loop:
```powershell
for ($i = 10; $i -gt 0; $i--) {  # 10-second countdown instead of 5
```

### Adding Multiple Commands
Use line breaks in the command string:
```powershell
$command = @"
command1
command2
command3
"@
```

### Removing the Enter Key Press
Comment out or remove this line if you don't want to automatically press Enter:
```powershell
# [System.Windows.Forms.SendKeys]::SendWait("{ENTER}")
```

## Licence

This script is provided as-is for educational and administrative purposes. Use at your own risk and ensure compliance with your organisation's policies.

## Contributing

Feel free to modify and improve this script for your specific use cases. Consider adding error handling, logging, or additional automation features as needed.
