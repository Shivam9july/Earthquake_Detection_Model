TremorWatch: Earthquake Precursor Detection System
Use seismic data to detect precursors to earthquakes in real-time

Overview
TremorWatch is a prototype system that continuously monitors real-time seismic waveform data from global stations and uses machine learning to detect potential P-wave precursors. By recognizing these early seismic signals, the system aims to provide a foundation for affordable, scalable, and automated early-warning earthquake detection.

How It Works
Continuously ingests seismic data streams from worldwide sensors.

Applies signal filtering and machine learning for pattern detection.

Identifies and flags P-wave and possible precursor activity in real-time.

P-Waves, S-Waves & Precursors
P-waves: The first seismic waves in an earthquake. They are compressional and travel fastest through the Earth's crust.

S-waves: Secondary waves, arriving after P-waves. <img width="1920" height="1080" alt="Screenshot 2025-08-07 235356" src="https://github.com/user-attachments/assets/e15417b4-3be1-47d1-a32d-63de382af9cf" />
They are slower but usually more destructive.

Precursors: Signs or signals before an earthquake, potentially indicating imminent seismic activity. These may include:

Microseismic activity

Changes in ground deformation

Anomalous waveform patterns

Example Output
The system prints detection results in real-time, such as:

text
No precursor [confidence: 1.00]  Time window: 0.0s – 3.0s
...
P-wave detected [confidence: 1.00]  Time window: 93.0s – 96.0s
[imageodel Evaluation

Metric	Value	Class
Accuracy	80%	Model-wide
Precision	99%	P-wave Class
Recall	60%	P-wave Class
F1 Score	67.7%	P-wave Class
Installation
Clone the repository:

Install dependencies:

text
pip install -r requirements.txt
Configure sensor sources and model options as described in /docs/SETUP.md.

Usage
Run a live detection simulation (after setup):

text
python tremorwatch.py --config config.yaml
Customize sensor endpoints and detection thresholds in the configuration.

View logs for real-time alerts or integrate with notification systems.
<img width="1920" height="1080" alt="Screenshot 2025-08-07 235314" src="https://github.com/user-attachments/assets/6325bfa0-e4ab-45c0-b5a6-4e43127119c0" />

License
This project is licensed under the MIT License.

Contact
Maintained by shivammaurya92000@gmail.com.
