# Network Port Scanner and Threats Visualizer
**Author:** Suhani Bhosale

## Project description
A cybersecurity learning project that checks a small, specified list of TCP ports on `localhost` or a private IPv4 address, labels detected open services with rules-based review guidance, and creates a CSV report plus a PNG visualization.

This is a basic educational triage aid—not a full vulnerability scanner. An open port does not by itself prove that a host is vulnerable, and a closed/filtered result cannot distinguish a firewall drop from a closed service.

## Features
- TCP connect scan using Python's standard `socket` module
- Restricts targets to loopback/private IPv4 addresses
- Small default list of common service ports; supports a custom port list
- Rules-based priority labels and human-readable notes
- Exports `scan_results.csv` and `threats_visualization.png`

## Technologies
- Python 3.10+
- `socket`, `ipaddress`, `argparse`, `time` (Python standard library)
- pandas for tabular results
- matplotlib for visualization
- Jupyter Notebook (`.ipynb`) for the notebook deliverable

## Dataset
No external dataset is required. The scanner produces its own scan-result dataset (`output/scan_results.csv`) when run. Port/service descriptions and review notes are small, manually defined educational rules in the code. For background reading, see the [Python socket documentation](https://docs.python.org/3/library/socket.html) and [Nmap port-scanning overview](https://nmap.org/book/port-scanning.html).

## Setup
```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
```

## Run
Scan the local computer (safe default):
```bash
python network_port_scanner.py
```

Specify ports on localhost:
```bash
python network_port_scanner.py --target 127.0.0.1 --ports 22,80,443,8080
```

Scan a private IPv4 device only when you own it or have written permission:
```bash
python network_port_scanner.py --target 192.168.1.10 --ports 22,80,443
```

Open `Suhani Bhosale_Network_Port_Scanner_Threats_Visualizer.ipynb` in Jupyter and run cells from top to bottom. The notebook runs a localhost demo.

## Output
- `output/scan_results.csv` — one row per scanned port
- `output/threats_visualization.png` — port-state and open-port review-priority charts

## Safety and limitations
- Use only on systems you own or have explicit authorization to assess.
- This project intentionally rejects public IPv4 targets and hostnames.
- Only TCP is checked; UDP, service/version detection, exploit testing, and vulnerability verification are not implemented.
- `closed_or_filtered` means the connection did not succeed; it does not prove the port is closed.
- Risk labels are generic review prompts, not a definitive severity score.

## GitHub
Create a repository named `Network-Port-Scanner-Threats-Visualizer`, upload these files, and replace this line with your repository URL once published. A repository cannot be published on your behalf without access to your GitHub account.
