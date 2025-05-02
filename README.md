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

## Task 2 -- GNSS in Urban Areas  
**Objective**: Improve GNSS positioning performance in urban environments using skymask data.  
- **Ground Truth**:  
  - Latitude: `22.3198722°`  
  - Longitude: `114.209101777778°`  
  - Altitude: `3.0 m`  
- **Description**:  
  - This function is a critical component of the **postnavigation phase**, designed based on the method of Non-Line-of-Sight (NLOS).  
  - Applies a sky mask to isolate the sky region from input data (satellite azimuth and elevation angles) collected during navigation.  
  - Filters out non-sky elements to produce **cleaner and more relevant data** for downstream processing.  
- **Key Features**:  
  - Masking and filtering of irrelevant environmental components.  
  - Enhances the reliability of subsequent computations.  
- **Role in Workflow**:  
  - The filtered sky data output from this function is used to inform and refine subsequent tasks—particularly the WLS positioning process in Task 3.  

## Task 3 -- RAIM  
**Objective**: Develop a classic weighted RAIM algorithm to detect and exclude faulty GNSS measurements.  
- **File**: `leastSquarePos.m`  
- **Functionality**:  
  - Executes **Weighted Least Squares (WLS)** calculations.  
  - Integrates **Receiver Autonomous Integrity Monitoring (RAIM)** to evaluate and ensure the reliability of positioning results.  
- **Description**:  
  - The `leastSquarePos.m` file optimizes position estimates by leveraging WLS algorithms.  
  - Operates on data refined through the `chi2_detector` process, enabling more accurate and noise-resilient calculations.  
  - The inclusion of the **RAIM algorithm** strengthens system integrity by detecting and mitigating potential positioning errors.  
- **Key Features**:  
  - Built-in RAIM for integrity monitoring and error detection.  
- **Role in Workflow**:  
  - This function is typically called **after sky masking** (Task 2), using cleaner input data to enhance accuracy and integrity in the computed navigation solution.  



## Task 4 -- Challenges of Using LEO Satellites for GNSS Navigation

Low Earth Orbit (LEO) satellites, operating at 500–2,000 km, are pivotal in communication systems like Starlink, offering low latency and high data rates. However, adapting these satellites for Global Navigation Satellite Systems (GNSS) introduces formidable challenges compared to Medium Earth Orbit (MEO) constellations like GPS or Galileo. This essay explores four primary challenges—rapid satellite motion, limited coverage, signal design constraints, and infrastructure demands—using real-life examples to illustrate their impact.  

### 1. Rapid Satellite Motion  
LEO satellites travel at **7–8 km/s**, resulting in **5–15-minute visibility windows** and **Doppler shifts exceeding 50 kHz**.  
- **Technical Impact**:  
  - **Signal Lock Challenges**: Low-cost GNSS receivers (e.g., MediaTek MT3333) struggle to track rapidly moving satellites.  
  - **Computational Overhead**: Compensating for Doppler shifts increases processing time by 40%, draining smartphone batteries.  
  - **Comparison with MEO**: GPS satellites (20,000 km altitude) move slower, enabling stable signal tracking for agricultural machinery.  

### 2. Limited Coverage and Constellation Size  
LEO satellites have **smaller coverage footprints** (~1,000 km diameter) than MEO satellites (~12,000 km).  
- **Technical Impact**:  
  - **Constellation Scalability**: A global LEO GNSS requires **3,000–5,000 satellites**, compared to 24–30 for MEO systems.  
  - **Orbit Maintenance**: Atmospheric drag at LEO reduces satellite lifespans to **5–7 years**, necessitating frequent replacements.  
  - **Comparison with MEO**: Galileo’s MEO constellation provided uninterrupted coverage during the 2021 Suez Canal blockage.
 
**Conclusion**  
LEO satellites face insurmountable hurdles in matching MEO GNSS performance. Rapid motion disrupts signal tracking, limited coverage demands unsustainable constellations, signal designs lack ranging optimization, and infrastructure costs are prohibitive. Until breakthroughs in clock miniaturization, signal redesign, and mega-constellation economics emerge, MEO systems like GPS will remain the backbone of global navigation.  
