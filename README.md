# Self Phone Three Positions Dataset

This repository contains an anonymized smartphone-based human activity recognition dataset collected from three common phone-carrying positions. The dataset is intended for research on position generalization, cross-position transfer, few-shot adaptation, and lightweight HAR models for edge-device scenarios.

## Dataset Overview

- Dataset name: Self Phone Three Positions Dataset
- Task: Human Activity Recognition (HAR)
- Sensor source: Smartphone inertial and motion sensors
- Participants: 36 anonymized participants
- Phone positions: hand, pants pocket, upper pocket, plus several additional carrying-condition folders retained from the original collection
- Activity classes: downstairs, running, sit-to-stand, sitting, stand-to-sit, standing, upstairs, walking
- File format: CSV
- Public version size: 696 CSV files
- Audio files: not included

## Directory Structure

```text
self_phone_three_positions_public/
  README.md
  participant_summary_public.csv
  raw/
    participant_001/
      hand/
        walking/
          trial_01.csv
      pants_pocket/
        walking/
          trial_01.csv
      upper_pocket/
        walking/
          trial_01.csv
    participant_002/
      ...
```

Each CSV file corresponds to one activity trial from one anonymized participant under one phone-carrying position.

## CSV Columns

The public CSV files retain only relative timing, sensor measurements, and activity labels. Privacy-sensitive fields such as absolute timestamps, GPS information, audio paths, gender folders, and demographic subject identifiers have been removed.

Main columns include:

- `elapsedMillis`: relative time since the beginning of the trial, in milliseconds
- `actionKeyword`: activity name recorded during collection
- `accelerometerAccelerationX/Y/Z`: accelerometer readings
- `gyroRotationX/Y/Z`: gyroscope readings
- `magnetometerX/Y/Z`: magnetometer readings
- `motionYaw`, `motionRoll`, `motionPitch`: device attitude estimates
- `motionRotationRateX/Y/Z`: motion rotation rate
- `motionUserAccelerationX/Y/Z`: user acceleration
- `motionGravityX/Y/Z`: gravity vector
- `motionMagneticFieldX/Y/Z`: magnetic field from motion framework
- `label`: activity label used for HAR classification

## Anonymization

The public version was anonymized before release:

- Original gender folders were removed.
- Original subject folders containing demographic information were replaced with `participant_001`, `participant_002`, etc.
- Collection dates and absolute timestamps were removed from file names and CSV contents.
- GPS/location fields were removed.
- Audio paths and all `.m4a` files were removed.
- A private subject-mapping file was generated outside this public folder and should not be uploaded.

## Recommended Experimental Use

This dataset can be used for:

- Leave-one-position-out (LOPO) cross-position generalization
- Leave-one-subject-out (LOSO) cross-user generalization
- K-shot target-position or target-user adaptation
- Contrastive learning for position-invariant HAR
- Knowledge distillation for compact edge-deployable HAR models

For few-shot experiments, report the value of `K` clearly, because using target-domain support samples is different from zero-shot cross-domain evaluation.

## Notes

The directory names preserve activity and phone-position labels because they are required for supervised HAR experiments. Participant identities and private demographic information are not included in this public version.

## Citation

If you use this dataset in a paper, please cite the corresponding paper or project once it is available.
