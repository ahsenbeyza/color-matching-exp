# Color-Word Matching Experiment

## Overview
This repository contains the implementation of a Color-Word Matching Experiment, a modified Stroop task designed to study selective attention under different distraction conditions. The experiment presents participants with a 3x3 grid of color names displayed in various font colors, where they must click the word whose text matches its font color (e.g., "blue" in blue). The experiment includes practice trials and three main conditions: no-notification (baseline), auditory distraction, and visual distraction (mimicking smartphone notifications). The project was developed using PsychoPy (version 2024.2.4) and is detailed in the report by Ahsen Beyza Özkul and İlayda Kara (May 2025).

## Experiment Structure
The experiment consists of the following components:

1. **Intro**: Displays a welcome message with a background image.
2. **Instructions**: Presents task instructions for 3 seconds, followed by a "Press space when ready" prompt.
3. **Practice Trials**: A loop of 5 trials with feedback ("Correct!" or "Incorrect!") to familiarize participants with the task.
4. **Main Trials**:
   - **No-Notification Condition**: 10 trials with a 3x3 grid and mouse clicks, no distractions.
   - **Auditory Condition**: Up to 28 trials with a random sound (0.5 seconds, played between 500-2000 ms).
   - **Visual Condition**: Up to 30 trials with a single text/image notification (e.g., "Mom: Don't forget milk!") at fixed coordinates (0.4, 0.4).
5. **Breaks**: Two 10-second breaks with a text prompt and keyboard input.
6. **End Screen**: A thank-you message displayed for 5-10 seconds.

## Data Collection
The experiment collects the following data, saved as CSV files per participant:
- **Demographics**: Age, gender, hours slept, color vision issues, and social media app usage.
- **Experiment Metadata**: Session ID, date, time, PsychoPy version, and display frame rate.
- **Trial Data**: Stimuli (words and colors), correct stimulus, mouse click coordinates, clicked cell, reaction time, button state, and accuracy (correct/incorrect clicks).
- **Feedback**: Timestamps for feedback display during practice trials.

## Setup Instructions
### Prerequisites
- **PsychoPy**: Version 2024.2.4 or compatible. Install via `pip install psychopy` or download from [psychopy.org](https://www.psychopy.org).
- **Python**: Version compatible with PsychoPy (e.g., Python 3.8+).
- **Hardware**: Computer with a display refresh rate of approximately 120 Hz.

### Installation
1. Clone this repository:
   ```bash
   git clone <repository-url>
   ```
2. Navigate to the project directory:
   ```bash
   cd color-word-matching-experiment
   ```
3. Ensure PsychoPy is installed:
   ```bash
   pip install psychopy
   ```
4. Place the condition files (Excel/CSV) in the project directory as specified in the PsychoPy experiment configuration.

### Running the Experiment
1. Open the PsychoPy Builder interface.
2. Load the `.psyexp` file included in the repository.
3. Configure the condition files (Excel/CSV) for practice and main trials in the respective loops (`PracticeLoop`, `NoNotifLoop`, `AuditoryLoop`, `VisualLoop`).
4. Run the experiment through PsychoPy’s Runner or via the command line:
   ```bash
   psychopy <experiment-file>.psyexp
   ```
5. Follow the on-screen instructions to complete the demographic form, practice trials, and main trials.

## Code Details
The experiment uses PsychoPy’s Builder interface with custom Python code components for trial logic:
- **Grid Setup**: A 3x3 grid is created with positions defined as `[-0.3, 0.3], [0, 0.3], [0.3, 0.3], ...`. Stimuli (words and colors) are pulled from condition files.
- **Mouse Input**: Tracks clicks on grid cells, logging coordinates, clicked cell names, and reaction times.
- **Feedback**: Displays "Correct!" or "Incorrect!" based on `correct_clicks` and `wrong_clicks` calculated in the code components.
- **Auditory Distraction**: Plays a 0.5-second sound at a random time (500-2000 ms) using a `Sound` component.
- **Visual Distraction**: Displays a single text/image notification at fixed coordinates (0.4, 0.4) per trial.

## Notes on Implementation
- **Changes from Initial Design**:
  - Condition files replaced code-generated grids for reliable stimulus randomization.
  - Visual notifications were fixed at (0.4, 0.4) instead of randomized, reducing distraction impact but improving reliability.
  - Feedback duration extended to 2 seconds for clarity.
  - Added a PsychoPy form for demographic data collection.
- **Known Issues**:
  - Loop errors led to extra trials in auditory (up to 28) and visual (up to 30) conditions.
  - Yellow stimuli feedback was missing, and brown appeared purple-brown.
  - Fixed notification placement reduced the effectiveness of visual distractions.

## Contributing
Contributions are welcome! Please submit a pull request or open an issue to suggest improvements, such as:
- Randomizing visual notification placement.
- Fixing loop errors to ensure exactly 10 trials per condition.
- Correcting color display issues (e.g., brown appearing purple-brown).

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact
For questions or feedback, contact the authors:
- Ahsen Beyza Özkul
- İlayda Kara
