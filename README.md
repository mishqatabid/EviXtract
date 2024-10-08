# EviXtract - Digital Forensics Tool

Designed to acquire, image, and analyze storage devices while performing metadata extraction, network traffic capture, and log analysis. This tool supports digital forensic investigations by helping investigators systematically collect, preserve, and analyze digital evidence.

## Key Features
- **Data Acquisition**: Captures raw data from a storage device using the `dd` command for forensic analysis.
- **Disk Imaging**: Creates a forensically sound image of a storage device to preserve evidence.
- **Filesystem Analysis**: Analyzes the filesystem to list and recover files from the disk image.
- **Metadata Extraction**: Extracts metadata such as creation, modification, access times, file size, and permissions.
- **Network Packet Capture**: Captures network traffic and saves suspicious packets for analysis.
- **Log Analysis**: Scans system logs for suspicious activities based on predefined attack patterns.


## Sample Data
The following sample data is used for testing and demonstration purposes:
- mydisk.dd: Sample raw data from a storage device.
- output.img: Sample disk image created for analysis.
suspicious_logs.txt: Sample log file containing detected suspicious activities.


## Modules Overview

### `acquire.py`
- **Purpose**: Acquire raw data from a specified device.
- **Function**: Uses the `dd` command to copy data from the device to a specified output file.

### `imaging.py`
- **Purpose**: Create a disk image of the acquired data.
- **Function**: Uses the `dd` command to generate a forensically sound image of the device.

### `analysis.py`
- **Purpose**: Analyze the filesystem of the disk image.
- **Function**: Utilizes the `pytsk3` library to identify files and directories in the disk image, listing their paths.

### `metadata-extract.py`
- **Purpose**: Extract metadata from files in the disk image.
- **Function**: Uses the `os.stat` function to gather file metadata, such as creation, modification, and access times.

### `capture.py`
- **Purpose**: Capture network packets for analysis.
- **Function**: Uses `scapy` to sniff and capture network traffic, saving it to a `.pcap` file for further analysis.

### `log-analyzer.py`
- **Purpose**: Analyze system logs for suspicious activity.
- **Function**: Scans logs using regular expressions to detect common attack patterns and indicators of compromise (e.g., failed login attempts, port scans, malware detection).

### `main.py`
- **Purpose**: Command-line interface to integrate all modules.
- **Function**: Provides options to run each module individually or in combination, allowing the investigator to perform various forensic tasks.



## Commands

1. **Acquire Data from a Device**:
   ```bash
   python3 main.py --acquire --device mydisk.dd --output test.img
   ```
   Acquires raw data from the device `mydisk.dd` and stores it in `test.img`.

2. **Create a Disk Image**:
   ```bash
   python3 main.py --imaging --device mydisk.dd --output forensic.img
   ```
   Creates a forensically sound disk image from the device `mydisk.dd`.

3. **Analyze the Filesystem**:
   ```bash
   python3 main.py --analyze --input output.img
   ```
   Scans the disk image to list all files and directories in the filesystem.

4. **Extract Metadata**:
   ```bash
   python3 main.py --extract-metadata --input output.img
   ```
   Extracts file metadata (creation time, modification time, etc.) from the files in the disk image.

5. **Capture Network Packets**:
   ```bash
   python3 main.py --capture --packet-count 10 --packet-output capture.pcap
   ```
   Captures 10 network packets and saves them in `capture.pcap` for analysis.

6. **Analyze System Logs**:
   ```bash
   python3 main.py --log-analysis --log-file syslog.log --output suspicious_logs.txt
   ```
   Scans `syslog.log` for suspicious patterns (e.g., failed login attempts, port scans) and saves the results in `suspicious_logs.txt`.


