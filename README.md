# Train_ticketing_goal_programming
Train Ticketing Optimization Model Objective: Maximize customer satisfaction while respecting capacity constraints
Here is a clean, scannable `README.md` tailored for your Train Ticketing Optimization Model:

---

# Train Ticketing Optimization Model

An intelligent seat allocation and confirmation system designed to maximize customer satisfaction and revenue while strictly respecting train segment capacity constraints.

## Features

* **Multi-Criteria Prioritization:** Calculates a composite utility score for each customer using normalized factors:
* Priority score (with passenger type multipliers like Seniors and Business travelers)
* Fare willingness (revenue potential)
* Booking time (rewards early bookings)
* Journey distance
* Group size penalties (prioritizes easier-to-accommodate smaller groups)


* **Segment-Based Capacity Tracking:** Monitors and enforces capacity limitations across individual station-to-station segments, preventing overbooking.
* **Greedy Optimization Algorithm:** Efficiently allocates seats to high-utility booking requests first.
* **Automated Analytics:** Generates comprehensive post-run reports breaking down booking statistics, passenger impacts, revenue capture rates, and heavily utilized route segments.

---

## Technical Stack

* **Language:** Python 3.x
* **Core Libraries:** `pandas`, `numpy`

---

## Quick Start

### 1. Installation

Ensure you have the required dependencies installed:

```bash
pip install pandas numpy

```

### 2. Usage

You can run the script directly to see a demonstration with synthetic data:

```python
from datetime import datetime
# Assuming the main class is in ticket_optimizer.py
from ticket_optimizer import TrainTicketOptimizer

# Initialize the optimizer with a capacity of 200 per segment
optimizer = TrainTicketOptimizer(train_capacity=200)

# Generate synthetic booking data for 100 customers across 20 stations
customers = optimizer.generate_customer_data(num_customers=100, num_stations=20)

# Run the optimization greedy allocation
results = optimizer.optimize_ticket_allocation()

# Print out the performance and breakdown report
optimizer.generate_report()

# Export results to CSV
optimizer.optimization_results['allocation_details'].to_csv('optimization_results.csv', index=False)

```

---

## Output Metrics

The model automatically tracks and outputs:

* **Basic Statistics:** Total requests, confirmation/rejection percentages.
* **Passenger Impact:** Exact count of confirmed vs. rejected passengers.
* **Revenue Analysis:** Total captured revenue vs. lost revenue, plus your overall revenue capture rate.
* **Demographic Breakdown:** Demographics success rates (Students, Seniors, Business, Regular, Tourists).
* **Bottleneck Analysis:** The top 5 most highly utilized train segments to help pinpoint capacity strains.
