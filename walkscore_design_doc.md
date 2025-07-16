# WalkScore Calculation System Design Document

## Overview
The WalkScore calculation system is designed to evaluate the walkability of locations in Toronto by analyzing various factors that contribute to pedestrian-friendly environments. The system processes crime data and calculates a comprehensive walkscore for each location, helping to understand the relationship between walkability and crime patterns.

## System Components

### 1. WalkScore Calculator
The core component that calculates walkability scores based on multiple factors:

#### 1.1 Points of Interest (POI) Score (40% of total score)
Evaluates the accessibility and variety of nearby amenities:

**Amenities and Weights:**
- Schools (5 points) - Essential for families and education
- Universities (4 points) - Important for students and education
- Restaurants (4 points) - Daily needs and social life
- Cafes (3 points) - Social gathering and work spaces
- Bars (2 points) - Entertainment and social life
- Hospitals (5 points) - Critical healthcare access
- Pharmacies (4 points) - Essential healthcare services
- Libraries (3 points) - Education and community resources
- Marketplaces (4 points) - Daily shopping needs
- Post Offices (2 points) - Essential services
- Banks (3 points) - Financial services
- Medical Services (4 points) - Healthcare access
- Community Centers (3 points) - Social and recreational activities

**Retail and Shopping (Shop):**
- Supermarkets (5 points) - Essential daily shopping
- Convenience Stores (4 points) - Quick access to necessities
- Bakeries (3 points) - Food and local businesses
- Clothing Stores (2 points) - Retail needs
- Department Stores (3 points) - Major shopping destinations

**Leisure Facilities:**
- Parks (5 points) - Green spaces and recreation
- Fitness Centers (3 points) - Health and wellness
- Sports Centers (3 points) - Sports and recreation
- Swimming Pools (3 points) - Recreational facilities

#### 1.2 Transit Score (20% of total score)
Evaluates public transportation accessibility:

**Transit Points and Weights:**
- Subway Entrances (5 points) - Major transit hubs
- Train Stations (5 points) - Major transit connections
- Light Rail Stops (4 points) - Medium-capacity transit
- Tram Stops (4 points) - Local transit
- Bus Stations (3 points) - Bus transit hubs
- Bus Stops (2 points) - Local bus service

#### 1.3 Pedestrian Infrastructure Score (20% of total score)
Assesses the quality and availability of pedestrian facilities:

**Components:**
- Sidewalk coverage
- Pedestrian pathways
- Crosswalks
- Pedestrian-friendly streets

The score considers:
- Density of pedestrian infrastructure
- Coverage ratio of pedestrian facilities
- Quality of walking paths

#### 1.4 Connectivity Score (20% of total score)
Evaluates the street network's walkability:

**Factors:**
- Intersection density
- Street connectivity
- Network completeness

## Calculation Process

### 1. Data Collection
- Uses OpenStreetMap (OSM) data through the OSMnx library
- Collects data within a 500-meter radius of each location
- Projects coordinates to Toronto's local coordinate system (UTM Zone 17N)

### 2. Score Calculation
1. **POI Score:**
   - Identifies all points of interest within radius
   - Applies distance decay (closer = higher weight)
   - Sums weighted scores and normalizes to 0-100

2. **Transit Score:**
   - Maps all transit points within radius
   - Applies distance-based weighting
   - Normalizes to 0-100 scale

3. **Pedestrian Score:**
   - Calculates pedestrian infrastructure density
   - Measures coverage ratio of pedestrian facilities
   - Combines metrics for final score

4. **Connectivity Score:**
   - Measures intersection density
   - Evaluates street network completeness
   - Normalizes to 0-100 scale

### 3. Final WalkScore
- Weighted average of all component scores:
  - POI Score: 40%
  - Transit Score: 20%
  - Pedestrian Score: 20%
  - Connectivity Score: 20%

## Technical Implementation

### Data Processing
- Uses pandas for data manipulation
- OSMnx for OpenStreetMap data retrieval
- Shapely for geometric calculations
- NetworkX for network analysis

### Error Handling
- Implements retry mechanisms for API calls
- Handles missing or invalid data
- Provides detailed error logging

### Performance Optimization
- Implements batch processing for large datasets
- Uses efficient data structures for calculations
- Implements caching for frequently accessed data

