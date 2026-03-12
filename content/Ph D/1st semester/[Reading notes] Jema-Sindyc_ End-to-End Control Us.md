---
title: >-
  [Reading notes] Jema-Sindyc: End-to-End Control Using Joint Embedding
  Multimodal
updated: 2025-08-02 11:51:07Z
created: 2025-07-29 14:43:27Z
latitude: 22.64839560
longitude: 120.32620850
altitude: 0.0000
---

[Reading notes] Jema-Sindyc: End-to-End Control Using Joint Embedding Multimodal Alignment in Directed Energy Deposition

---
- Tinkerforge is for what? free?
- Sync different pc can use Network time protocol

- using NAS to store the data in bag format
- choosing Laser Power [200, 800], step is 200 w, r andomly
- with 4 different velocity.


Q. why directly select the Laser Power density.?
make sure the experiment dataset is wide enough.

- Post trained model是指什麼？pre-trained model的差別

- pairwise Squares and. similarity is relative? brentchang

training data-> (training, validate, testing)=80, 10, 10

-----

Using SINDY
to get the next melt Pool Length by the. Laser Power and MP length currently. => just like derivative the state function

Target: to use the cost function to find the Optimal laser power
=> desired Melt Pool length