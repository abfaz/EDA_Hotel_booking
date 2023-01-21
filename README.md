# EDA_Hotel_booking

## Objective
A dataset containing 119390 records across 32 features has been given with information regarding bookings of two hotels from July 2015 to August 2017. These two hotels are City Hotel and Resort Hotel.
The main objective behind this project is to explore and analyze data to discover important factors that govern the bookings and give insights to hotel management.

## Dataset
The dataset consist of following columns (features):

```
- hotel: Name of hotel ( City or Resort)
- is_canceled: Whether the booking is canceled or not (0 for no canceled and 1 for canceled)
- lead_time: time (in days) between booking transaction and actual arrival.
- arrival_date_year: Year of arrival
- arrival_date_month: month of arrival
- arrival_date_week_number: week number of arrival date.
- arrival_date_day_of_month: Day of month of arrival date
- stays_in_weekend_nights: No. of weekend nights spent in a hotel
- stays_in_week_nights: No. of weeknights spent in a hotel
- adults: No. of adults in single booking record.
- children: No. of children in single booking record.
- babies: No. of babies in single booking record. 
- meal: Type of meal chosen 
- country: Country of origin of customers (as mentioned by them)
- market_segment: What segment via booking was made and for what purpose.
- distribution_channel: Via which medium booking was made.
- is_repeated_guest: Whether the customer has made any booking before(0 for No and 1 for 
                     Yes)
- previous_cancellations: No. of previous canceled bookings.
- previous_bookings_not_canceled: No. of previous non-canceled bookings.
- reserved_room_type: Room type reserved by a customer.
- assigned_room_type: Room type assigned to the customer.
- booking_changes: No. of booking changes done by customers
- deposit_type: Type of deposit at the time of making a booking (No deposit/ Refundable/ No refund)
- agent: Id of agent for booking
- company: Id of the company making a booking
- days_in_waiting_list: No. of days on waiting list.
- customer_type: Type of customer(Transient, Group, etc.)
- adr: Average Daily rate.
- required_car_parking_spaces: No. of car parking asked in booking
- total_of_special_requests: total no. of special request.
- reservation_status: Whether a customer has checked out or canceled,or not showed 
- reservation_status_date: Date of making reservation status.
```

## Data Cleaning and Feature Engineering

### (1) Removing Duplicate rows
All duplicate rows were dropped.

### (2) Handling null values
- Null values in columns `company` and `agent` were replaced by 0.
- Null values in column `country` were replaced by 'others'.
- Null values in column `children` were replaced by the mean of the column.
  

### (3) Converting columns to appropriate data types

- Changed data type of `children`, `company`, `agent` to int type.
- Changed data type of `reservation_status_date` to date type.

### (4) Creating new columns
- Created new column `total_stay` by adding `stays_in_weekend_nights`+`stays_in_week_nights`.
- Created new column `total_people` by adding `adults`+`children`+`babies`.
- Created new column `same_room` for checking if the reserved room type and assigned room type are same(1) or not(0).


### (5) Category columns like hotel, meal, country, etc has been stored into variable cat_cols and Numeric columns is stored into variable num_cols for EDA.

## Exploratory Data Analysis

EDA was carried out in 3 steps:

### Univariate Analysis
Univariate analysis is the simplest form of analyzing data. Uni means one, so in other words the data has only one variable. Univariate data requires to analyze each variable separately. Here we analyse the pieplots and barplots of each variable present in cat_cols (category columns).

### Bivariate Analysis
Bi means two and variate means variable, so here there are two variables. The analysis is related to cause and the relationship between the two variables. So by performing bivariate analysis, we tried to answer the following questions:

Q1: Which hotel generates more revenue?
Q2: Which hotel has longer waiting time?
Q3: Which hotel has higher lead time?
Q4: Which hotel has higher booking cancellation rate?
Q5: Which hotel has higher chance that its customer will return for another stay?
Q6: Which hotel room types has better adr?
Q7: How long do people stay at the hotel?
Q8: Which distribution channel has longest average waiting time?
Q9: Which distribution channel has longest lead time?
Q10: Which distribution channel has highest booking cancellation rate?
Q11: Which is the most visiting month?
Q12: Which month produces highest adr?

### Correlation Analysis
It is used to measure the strength of the linear relationship between two variables and compute their association. Correlation analysis calculates the level of change in one variable due to the change in the other. Correlation analysis of the dataset was carried out using a correlation heatmap with the non categorical or Numerical columns like lead time, arrival_date_year, etc.


## Conclusion
The following conclusions were drawn from analysis:
- 61% is city hotel and 39% is resort hotel.
- Most People (13%) arrived in the month of August.
- Most preferred (78%) meal type is BB (Bed and Breakfast).
- Most People (31%) are from Portugal, followed by Germany, France, etc.
- Most demanded room type is A.
- 65% People reserved room A but only 53% assigned the same room.
- 59% market segment used is online TA, followed by offline TA/TO.
- 28% booking is cancelled.
- 79% distribution channel is TA/TO.
- 26% reservations are cancelled by guests.
- only 4% are repeated guest.
- 88% have reserved and assigned same room.
- Agent 9 has made most booking.
- City type hotel has slightly higher mean_adr than resort type hotel. Therefore, city type hotel is making more revenue.
- City hotel has longer waiting time as it's busier than resort hotel.
- City hotel has slightly higher lead time.
- City type hotel has higher booking cancellation rate (30.10%) than resort type hotel (23.48%).
- Resort hotel has slightly higher chance that its customers will return for another stay.
- Room types H, G and C are better adr rooms.
- Most common stay length is less than 4  days and generally people prefer City hotel for short stay, but for long stays, Resort Hotel is preferred
- TA/TO channel has longest average waiting time. Therefore customer booked through TA/TO channel have to wait a little longer to confirm booking of rooms.
- TA/TO channel has longest  lead time. So customer using TA/TO channel planned their visit ahead of time. 
- TA/TO type channel has highest (~30%) booking cancellation rate.
- Most visitors come in the month of August.
- August month produces highest adr as this is the busiest month of the year.
- Within the year, average adr follows a trend as first it increases from beginning of the year and reaches at its peak in August and then decreases to end of the year.
- adr and total_people are positively correlated by 40%.
- total_stay and lead time are positively correlated by 32%
- adr and children are positively correlated by 35%.



