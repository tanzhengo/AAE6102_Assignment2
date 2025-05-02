# AAE6102_Assignment2
AAE6102 Satellite Communication and Navigation Assignment 2 Analysis

# GNSS Positioning Technologies Analysis

## Comparative Analysis of GNSS Methods for Mobile Devices

### Method Comparison Table

| Method  | Accuracy | Convergence | Infrastructure | Best Use Case | Limitations |
|---------|----------|-------------|----------------|---------------|-------------|
| DGNSS   | 1-3m     | Instant     | Reference stations | Urban navigation | Limited range from stations |
| RTK     | cm-level | Instant     | Base station (<20km) | AR applications | High power consumption |
| PPP     | dm-level | 10-30 min   | Global corrections | Remote areas | Slow initialization |
| PPP-RTK | cm-level | 2-5 min     | Sparse networks | Precision delivery | Complex integration |

### Key Features

#### Differential GNSS (DGNSS)
- ✅ Cost-effective urban positioning
- ✅ 1-3m accuracy in metropolitan areas
- 🚫 Performance degrades beyond 100km from reference

#### Real-Time Kinematic (RTK)
- ✅ Centimeter-level precision
- ✅ Essential for AR applications
- 🚫 Requires dense base station network

#### Precise Point Positioning (PPP)
- ✅ Global coverage
- ✅ Works in remote regions
- 🚫 30+ minute convergence time

#### PPP-RTK
- ✅ Combines PPP and RTK advantages
- ✅ Faster convergence than PPP
- 🚫 High data requirements

## Urban GNSS Enhancement

### Sky Mask Processing
```matlab
function cleanData = urbanGNSSFilter(rawData, skyMask)
    % Filters NLOS signals using azimuth/elevation mask
    cleanData = rawData(skyMask == 1,:);
end
