# Literature Review Matrix

| No | Paper | Domain | Method | Dataset | Metrics | Main Contribution | Limitation | Relevance |
|---|---|---|---|---|---|---|---|---|
| 1 | Smart occupancy detection network | Smart parking | Retinex + Attention + APOA + EDN | CNRPark + EXT | Accuracy, Precision, MCC | Detects parking occupancy with high accuracy | Heavy compute; limited dataset | High |
| 2 | Traffic flow perception system | Traffic / ITS | DuCRG-YOLOv11n + ByteTrack + LLMs | Kaggle + 1,000 real images + city APIs | FPS, Precision, Recall, F1, MOTA, IDF1, MOTP | Multimodal traffic perception and analysis | Missing context data; lighting/occlusion issues | Medium |
| 3 | Real-time slot allocation system | Smart parking reservation | ML + heuristic optimization | Live occupancy, arrival time, duration, vehicle size | Allocation efficiency, search time, throughput | Optimizes slot assignment and reduces search time | Can slow down under very large load | High |
| 4 | Autonomous parking simulation | Autonomous parking | Behavioral Cloning + PPO + DRL | Demonstration data + simulated parking env. | Success rate, collision rate, steps | Strong trajectory planning in simulation | Sim-to-real gap | High |
| 5 | Reservation-Based Smart Parking System | Smart parking reservation | Distributed reservation workflow | Slot states + reservation time + ETA | Success rate, waiting time, utilization | Simple booking workflow to reduce congestion | Limited gate automation | High |
| 6 | Automated multi-level parking system | Multi-level parking | Not available due access denial | Not available due access denial | Not available due access denial | Indicates an automated multi-level parking topic | Source blocked; details missing | High |
| 7 | Predictive Smart Parking Availability System | Smart parking prediction | Supervised ML + web + Google Maps | Historical parking data | Unit, integration, end-to-end tests | Predicts availability and supports booking | No mobile app; no real-time IoT sensors | High |
| 8 | Predictive Smart Parking Availability System | Smart parking prediction | Supervised ML + web + Google Maps | Historical parking data | Unit, integration, end-to-end tests | Web-based prediction and booking workflow | No mobile app; no real-time IoT sensors | High |
| 9 | IoT-Based Smart Parking System Using Deep Learning | Smart parking / IoT | CNN + IoT cloud sync | CCTV images, PKLot-style data | Accuracy, Precision, Recall, latency | Replaces per-slot sensors with camera-based detection | Occlusion reduces accuracy | Very High |
| 10 | Reservation-Based Smart Parking System | Smart parking reservation | Distributed reservation workflow | Slot states + reservation time + ETA | Success rate, waiting time, utilization | Reduces queueing at entrances | Older workflow; limited automation | High |




