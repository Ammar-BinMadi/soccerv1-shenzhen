📘 README — Soccer Tracking & Analytics Engine

Overview

This repository provides a modular Python framework for computer-vision-driven soccer analytics, including player tracking, ball tracking, event detection, and tactical visualization.
It is designed to integrate with Norfair, OpenCV, and custom geometry utilities to analyze broadcast-style match footage.

The system reconstructs match events frame-by-frame, detects passes, evaluates player–ball interactions, and visualizes tactical insights such as possession heatmaps and movement arcs.

⸻

✨ Features

🔵 Ball Tracking

ball.py
	•	Tracks the ball across video frames using Norfair detections.
	•	Maintains ball position, movement vectors, and possession logic.
	•	Detects when the ball changes direction or transitions between players.

🟢 Player Tracking

player.py
	•	Creates player objects with:
	•	2D field coordinates
	•	Team association
	•	Role classification (if provided)
	•	Handles nearest-player logic for ball control estimation.
	•	Provides utilities for loading player lists from predictions.

🟡 Team Representation

team.py
	•	Represents a team with:
	•	Team name
	•	Team color (used by Draw for visualization)
	•	Player roster
	•	Includes lookup utilities (e.g., find by name).

🔶 Pass Detection System

pass_event.py
	•	Defines a Pass event between two ball bounding boxes.
	•	Supports:
	•	Absolute path reconstruction
	•	Drawing pass trajectories on the pitch
	•	Accepts an external coordinate transformation system to convert image coordinates → pitch coordinates.

🎨 Visualization Engine

draw.py
	•	Provides drawing utilities using OpenCV, Pillow, and custom transforms.
	•	Renders:
	•	Player markers
	•	Team colors
	•	Ball positions
	•	Pass lines
	•	Motion trails
	•	Used heavily by the Match object for replay or live visualization.

⚽ Match Reconstruction Core

match.py
	•	Core engine that:
	•	Processes every frame
	•	Tracks players and ball simultaneously
	•	Computes possession time
	•	Detects passes
	•	Manages event sequencing
	•	Produces high-level analytics for downstream use.

🔗 Module Exports

__init__.py exposes:
	•	Ball, Draw, Match, Player, Team
for easy importing from the package root.
