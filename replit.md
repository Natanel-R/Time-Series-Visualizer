# Overview

This is a **Page View Time Series Visualizer** project from FreeCodeCamp's Data Analysis with Python curriculum. The application analyzes and visualizes page view data from the freeCodeCamp forum (May 2016 - December 2019) using Python data analysis libraries.

The project creates three types of visualizations:
1. A line plot showing daily page views over time
2. A bar chart displaying average monthly page views grouped by year
3. Box plots showing page view distributions by year and month

The code reads CSV data, cleans it by removing outliers (top and bottom 2.5%), and generates publication-ready charts using matplotlib, pandas, and seaborn.

# Recent Changes

**November 12, 2025**:
- Fixed Python version compatibility issue in `pyproject.toml` (changed from `^3.7` to `>=3.10,<4.0`)
- Fixed FutureWarning in `test_module.py` by updating deprecated pandas Series conversion
- Configured workflow to run tests and generate visualizations
- All 11 unit tests pass successfully

**Known Issues**:
- PendingDeprecationWarning from seaborn 0.13.2's internal boxplot implementation (not fixable in application code)

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Core Technology Stack

**Primary Language**: Python 3.10

**Data Analysis Libraries**:
- **pandas**: CSV data loading, manipulation, and time series operations
- **matplotlib**: Core plotting library for line and bar charts
- **seaborn**: Statistical visualization for box plots
- **NumPy**: (implicit dependency) Numerical operations support

**Design Pattern**: Script-based data analysis with function-based architecture

## Data Processing Pipeline

**Data Loading**: 
- CSV file reading with automatic date parsing
- Date column set as DataFrame index for time series operations
- Data structure: Single 'value' column with datetime index

**Data Cleaning Strategy**:
- Outlier removal using quantile-based filtering
- Removes values outside the 2.5th to 97.5th percentile range
- Preserves 95% of data centered around median

**Rationale**: Quantile-based filtering is standard practice for time series anomaly detection, removing extreme outliers while maintaining data distribution integrity.

## Visualization Architecture

**Three Visualization Functions**:

1. **Line Plot** (`draw_line_plot`):
   - Single time series line chart
   - Fixed dimensions (23x7 inches) for readability
   - Red line with 2pt width for visual emphasis
   - Labeled axes with descriptive title

2. **Bar Plot** (`draw_bar_plot`):
   - Monthly averages grouped by year
   - Data pivoting: Years on x-axis, months as grouped bars
   - Uses pandas plotting with legend for month identification
   - Unstacking transforms multi-index to column-based structure

3. **Box Plot** (`draw_box_plot`):
   - Distribution analysis by year and month
   - Uses seaborn for statistical visualization
   - Two side-by-side plots: yearly trend and monthly seasonality

**Output Strategy**: All plots saved as PNG files for persistence and sharing

## Testing Framework

**Unit Testing**:
- Built-in unittest framework
- Tests validate data cleaning, plot titles, labels, and data point counts
- Automatic test execution on script run
- Ensures output meets freeCodeCamp project specifications

**Test Coverage**:
- Data integrity (1238 data points after cleaning)
- Plot metadata (titles, axis labels)
- Legend accuracy (month names)

# External Dependencies

**Data Source**:
- CSV file: `fcc-forum-pageviews.csv`
- Contains datetime and page view value columns
- Expected to be in project root directory

**Python Package Dependencies**:
- matplotlib (visualization)
- pandas (data manipulation)
- seaborn (statistical plots)
- NumPy (implicit, via pandas/matplotlib)

**Development Environment**:
- Replit platform (Nix-based package management)
- Virtual environment managed via Replit infrastructure
- Legacy venv migrated to new Replit system

**No External APIs or Database Systems**: This is a standalone data analysis script with local file I/O only.