# TicketNest:Database System Management Course Project

## 1. Executive Summary
**TicketNest** is a comprehensive ticketing system simulating TicketMaster, designed for users, event organizers, and administrators to manage and interact with events, ticketing operations, and each other. **Users** can manage their preferences, purchase tickets, attend events, and submit reviews. **Event organizers** can create and manage events, configure various ticket types, and oversee ticket availability. **Administrators** handle customer service, including refunds, and analyze user activities and sales performance to optimize the platform’s operations. To facilitate these processes, the system includes essential entities such as **User**, **Event**, **Ticket**, **TicketType**, **Order**, **Preference**, **Reviews**, and **PaymentMethod**. This project allows for efficient event management, smooth ticket sales, and personalized user experiences.

## 2. Responsibilities
- In this project, my primary responsibilities included:
  - **Database Management**: Developed and maintained the database schema in MySQL and MongoDB with other teammates.
  - **SQL Query Optimization**: Designed and implemented SQL Query to generate event performance reports, calculating total tickets sold, revenue, and average ratings for a specified date range. Exported these reports as CSV files for detailed analysis.
  - **Front-end Development**: Created prototypes for user and administrator features with Budibase.
  - **Testing and Debugging**: Conducted thorough testing for all the user and administrator features, identified bugs, and resolved issues to ensure application stability and usability.
- My teammates included:
  - Yinuo Feng
  - Meihao Cheng
  - Jieling Gong

## 3. Budibase Deployed Link  
Budibase is a low-code platform that allows users to take control of the multiple datasets and rogue spreadsheets. In this project, we use Budibase to streamline the creation of a responsive and user-friendly interface. By integrating with both MySQL and MongoDB, Budibase facilitated seamless data management and dynamic interactions between relational and NoSQL databases. It allowed for rapid prototyping of user dashboards, event management pages, and administrative tools, while enabling efficient CRUD operations through pre-configured workflows. 
- link: https://cs5200group6.budibase.app/app/ticketnest#/user/login

## 4. Features Overview
### (1) User Features
- Create Account: Register with a username, email, and password.
- Log In: Access personalized features through secure authentication.
- Search for Events: Filter events by category, date, or keywords.
- View Event Details: Access detailed event descriptions, dates, venues, and ticket types.
- Purchase Tickets: Select ticket types and payment methods to secure event attendance.
- Order History: Track and review past and current orders.

### (2) Event Organizer Features
- Create Events: Add new events with names, dates, locations, and descriptions.
- Manage Tickets: Create, update, and categorize ticket types for events.
- Edit Event Details: Update event information for accuracy.
- View Events: Monitor events by status (active, past, or canceled).

### (3) Administrator Features
- Generate Performance Reports: View and export event performance data, including tickets sold, revenue, and ratings.
- Manage Refunds: Oversee customer service operations, including processing refunds.

## 5. Database Design
### (1) MySQL database design - ER Diagram
- link: https://www.drawdb.app/editor?shareId=35c1a18258f771a8d5ec26ec7ae8a5a9
- image:
![Untitled Diagram_2024-09-26T23_41_10 970Z](https://github.com/user-attachments/assets/bb7dbb3d-4b57-43a5-82dd-669c6e458ab7)

### (2) MongoDB database design
Our MongoDB collection has one document called "entities", which contains information
about aritists or sports team associated with events.

#### Schema Description
Here is the description of schema:
```
{
    "id": ObjectID
    "name": String  // artist or sports team name
    "type": String // "artist" or "team"
    "bio": String // biography for artist
    "genre": String // genres for artist
    "sport": String // type of sport for sport teams
    achievements: [
        {
            "title": String
            "date": Date
            "description": String
        } 
    ] // list of achievements for sports teams
    "stats": {
        "wins": Number
        "losses": Number
        "draws": Number
    } // statas for sports teams
    "wikipedia_link": String // wikipedia link (if applicable)
}
```
#### Example Documents
- artist
  - ```{"_id":{"$oid":"6733ac0501e79856596849d2"},"name":"Emily Bowen","type":"artist","bio":"Emily Bowen is an acclaimed indie folk singer known for her soulful lyrics.","genre":"Indie Folk","wikipedia_link":"https://en.wikipedia.org/wiki/Emily_Bowen"}```
  - ```{"_id":{"$oid":"6733ac0501e79856596849d3"},"name":"Norman Jackson","type":"artist","bio":"Norman Jackson is a rock guitarist with a passion for blues and jazz.","genre":"Rock","wikipedia_link":"https://en.wikipedia.org/wiki/Norman_Jackson"}```
  - ```{"_id":{"$oid":"6733ac0501e79856596849d4"},"name":"David Lewis","type":"artist","bio":"David Lewis is a classical pianist recognized for his mastery of Beethoven.","genre":"Classical","wikipedia_link":"https://en.wikipedia.org/wiki/David_Lewis"}```
- sports teams
  - ```{"_id":{"$oid":"6733ac0501e79856596849dc"},"name":"Jose Sanchez","type":"team","sport":"Soccer","achievements":[{"title":"League Champions","date":"2022-06-15","description":"Won the league championship after an impressive season."}],"stats":{"wins":{"$numberInt":"24"},"losses":{"$numberInt":"6"},"draws":{"$numberInt":"4"}},"wikipedia_link":"https://en.wikipedia.org/wiki/Jose_Sanchez_Soccer_Team"}```
  - ```{"_id":{"$oid":"6733ac0501e79856596849dd"},"name":"David Evans","type":"team","sport":"Basketball","achievements":[{"title":"Regional Champions","date":"2023-03-10","description":"Won the regional tournament."}],"stats":{"wins":{"$numberInt":"18"},"losses":{"$numberInt":"10"},"draws":{"$numberInt":"0"}},"wikipedia_link":"https://en.wikipedia.org/wiki/David_Evans_Basketball_Team"}```
  - ```{"_id":{"$oid":"6733ac0501e79856596849de"},"name":"Bryan Salazar","type":"team","sport":"Baseball","achievements":[{"title":"National Championship","date":"2021-09-21","description":"Claimed the national title after a stellar season."}],"stats":{"wins":{"$numberInt":"30"},"losses":{"$numberInt":"15"},"draws":{"$numberInt":"0"}},"wikipedia_link":"https://en.wikipedia.org/wiki/Bryan_Salazar_Baseball_Team"}```

## 6. User Manual
This project provides three main user roles: **Users**, **Event Organizers**, and **Administrators**, each with specific functionality accessible upon logging in. All features require users to be logged in.
### (1) User Guide

#### -(1) Login
- User Login Credentials
  - **Email**: user@gmail.com
  - **Password**: UserTest@123
After logging in, Users are redirected to the **Order History** page, where they can view past orders.

- Check Order History
  - Each order displays essential details, including **Order ID**, **Purchase Date**, **Order Status**, and **Payment Method**.
  - To view more details about an order, click the **Order Details** button at the bottom right of the order entry. This opens a detailed view showing:
    - Event information: date, venue, artist names
    - Ticket type and price
    - Total payment amount
  - To return to the **Order History** page, click **Go Back** in the bottom right corner.

#### -(2) Search for Events
Navigate to the **Search** option in the navigation bar to enter the **Events** page. Here, you can find events based on specific criteria:

- **Text Search**: Enter keywords related to the event name, artist name, or venue name in the search bar.
- **Category Filter**: Select an event category from **Concert**, **Festival**, **Sports Event**, or **Theatre**.
- **Status Filter**: Choose an event status from **Active**, **Past**, or **Canceled**.
- **Date Filter**: Choose a date range.

Events matching the criteria will be displayed with details such as **Event Date**, **Artist Name**, **Event Name**, **Venue**, **Category**, and **Event Status**.


#### -(3) Search for Entities
Navigate to the **Search** option in the navigation bar to enter the **Entity** page. Here, you can find artists and sports teams based on specific criteria:

- **Text Search**: Enter keywords related to the artist or team name in the search bar.
- **Category Filter**: Select an entity category from **Artist** or **Team**.
- **Genre Filter**: For artists only. Choose a music genre from **Alternative Rock**, **Classical**, **Country**, **Electronic**, **Indie Folk**, **Jazz**, **Opera**, **Pop**, or **Rock**.
- **Sport Filter**: For teams only. Choose a sport type from **Baseball**, **Basketball**, **Cricket**, **Football**, **Hockey**, **Rugby**, **Soccer**, **Swimming**, **Tennis**, or **Volleyball**.
  
#### -(4) View Event Details
- Next to each event, click **Find Details** to view the **Event Details** page. This page includes a description of the event, available ticket types, and prices.
- Click **Entity Details** on the **Event Details** page to view specific information about the artists or teams. This includes a bio for artists, achievements and stats for teams, and a Wikipedia link for both artists and teams.

#### -(5) Buy Tickets
On the **Event Details** page, Users can purchase tickets by following these steps:

- Click **Buy Tickets** at the bottom right.
- Choose the desired **ticket type**, **quantity**, and **payment method**.
- The page will automatically calculate and display the total payment amount.
- Click **Place Order** to complete the purchase.

### (2) Event Organizer Guide

#### -(1) Login
- Event Organizer Login Credentials
  - **Email**: organizer@gmail.com
  - **Password**: Organizer@1

#### -(2) Event Organizer Dashboard
Once logged in, Event Organizers are redirected to their **Dashboard**, which has three primary options:

1. **Manage Events**
2. **Manage Tickets**
3. **Manage Orders**

> **Note**: Event Organizers do not have access to **Order History** or **Buy Tickets** functionality.

### (3) Administrator Guide

#### -(1) Login
- Administrator Login Credentials
  - **Email**: administrator@gmail.com
  - **Password**: Administrator@1

#### -(2) Administrator Dashboard
Once logged in, Administrators are redirected to their **Homepage**, where they can access the event performance report page:

- **Generate Event Performance Report**: Generate and save a summary report of event performance for a specified date range. The administrator can select a start date and end date, then generate the event performance report for that period in the Report table. The report includes key details such as total tickets sold, revenue generated, and the average rating per event. This report helps assess the success of events and identify trends over time.
  - SQL Queries Used:
     ```sql
    DELIMITER //
    
    CREATE PROCEDURE GenerateEventPerformanceReport(IN startDate DATE, IN endDate DATE)
    BEGIN
        TRUNCATE TABLE Report;
    
        INSERT INTO Report (event_id, event_name, ticket_sold, revenue, avg_rating, event_date)
        SELECT e.event_id,
               e.event_name,
               CASE 
                   WHEN e.event_status = 'Canceled' THEN 0 
                   ELSE COALESCE(ticket_data.total_tickets_sold, 0) 
               END AS ticket_sold,
               CASE 
                   WHEN e.event_status = 'Canceled' THEN 0 
                   ELSE COALESCE(ticket_data.total_revenue, 0) 
               END AS revenue,
               COALESCE(AVG(r.rating), 0) AS avg_rating,
               e.date AS event_date
        FROM Event e
        LEFT JOIN (
            SELECT t.event_id,
                   SUM(ot.quantity_purchase) AS total_tickets_sold,
                   SUM(t.price * ot.quantity_purchase) AS total_revenue
            FROM OrderTicket ot
            INNER JOIN `Order` o ON ot.order_id = o.order_id
            INNER JOIN Ticket t ON ot.ticket_id = t.ticket_id
            WHERE o.order_status = 'Completed'
              AND o.purchase_date BETWEEN startDate AND endDate
            GROUP BY t.event_id
        ) AS ticket_data ON e.event_id = ticket_data.event_id
        LEFT JOIN Review r ON e.event_id = r.event_id
        GROUP BY e.event_id, e.event_name, e.date;
    
        SELECT * FROM Report;
    END //
    
    DELIMITER ;

