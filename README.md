
# Music Store SQL Database

## Overview

This project represents a music store database using SQL, as shown by the provided Entity Relationship (ER) diagram. It models key components of the system such as artists, albums, tracks, customers, invoices, employees, and playlists. Each table corresponds to an entity in the music store, connected through foreign keys to maintain relationships between the data.

---

## ER Diagram Components

### 1. **Artist**
   - **Fields**: `ArtistId`, `Name`
   - **Description**: Stores data on music artists.
   - **Relationships**: 
     - One-to-many with the `Album` table. Each artist can have multiple albums.

### 2. **Album**
   - **Fields**: `AlbumId`, `Title`, `ArtistId`
   - **Description**: Contains information about music albums.
   - **Relationships**: 
     - Belongs to an `Artist`, identified by the `ArtistId` foreign key.
     - Has a one-to-many relationship with the `Track` table.

### 3. **Track**
   - **Fields**: `TrackId`, `Name`, `AlbumId`, `MediaTypeId`, `GenreId`, `Composer`, `Milliseconds`, `Bytes`, `UnitPrice`
   - **Description**: Represents individual music tracks.
   - **Relationships**: 
     - Belongs to an `Album`.
     - Connected to `MediaType` and `Genre` through foreign keys.
     - One-to-many relationship with `InvoiceLine` and `PlaylistTrack`.

### 4. **MediaType**
   - **Fields**: `MediaTypeId`, `Name`
   - **Description**: Defines the media format of the tracks, such as MP3, WAV, etc.
   - **Relationships**: 
     - Connected to `Track` table with a one-to-many relationship.

### 5. **Genre**
   - **Fields**: `GenreId`, `Name`
   - **Description**: Categorizes the tracks into different genres like Rock, Jazz, etc.
   - **Relationships**: 
     - One-to-many relationship with the `Track` table.

### 6. **Playlist**
   - **Fields**: `PlaylistId`, `Name`
   - **Description**: Holds the playlists created by users.
   - **Relationships**: 
     - Many-to-many relationship with `Track` through the `PlaylistTrack` table.

### 7. **PlaylistTrack**
   - **Fields**: `PlaylistId`, `TrackId`
   - **Description**: Acts as a junction table that links playlists with tracks, implementing a many-to-many relationship.

### 8. **Invoice**
   - **Fields**: `InvoiceId`, `CustomerId`, `InvoiceDate`, `BillingAddress`, `BillingCity`, `BillingState`, `BillingCountry`, `BillingPostalCode`, `Total`
   - **Description**: Stores details of customer invoices.
   - **Relationships**: 
     - Connected to the `Customer` table through `CustomerId`.
     - One-to-many relationship with `InvoiceLine`.

### 9. **InvoiceLine**
   - **Fields**: `InvoiceLineId`, `InvoiceId`, `TrackId`, `UnitPrice`, `Quantity`
   - **Description**: Represents each line item in an invoice.
   - **Relationships**: 
     - Linked to `Invoice` and `Track`.

### 10. **Customer**
   - **Fields**: `CustomerId`, `FirstName`, `LastName`, `Company`, `Address`, `City`, `State`, `Country`, `PostalCode`, `Phone`, `Fax`, `Email`, `SupportRepId`
   - **Description**: Stores customer details.
   - **Relationships**: 
     - Connected to `Employee` through the `SupportRepId` field, indicating which employee supports each customer.
     - Has a one-to-many relationship with the `Invoice` table.

### 11. **Employee**
   - **Fields**: `EmployeeId`, `LastName`, `FirstName`, `Title`, `ReportsTo`, `BirthDate`, `HireDate`, `Address`, `City`, `State`, `Country`, `PostalCode`, `Phone`, `Fax`, `Email`
   - **Description**: Contains information about employees.
   - **Relationships**: 
     - Employees can report to other employees, creating a hierarchical structure.
     - Acts as a support representative for customers, linked through the `SupportRepId` in the `Customer` table.

---

## Usage

- This schema can be used in a relational database management system (RDBMS) like MySQL, PostgreSQL, or SQL Server.
- The relationships between tables are managed through foreign keys to ensure data integrity and allow for complex queries involving multiple tables.

---

## Key Features
- **Efficient Data Management**: All key components like Artists, Albums, Tracks, Customers, and Invoices are logically organized to minimize redundancy and improve performance.
- **Support for Music Playlists**: Users can create playlists containing multiple tracks.
- **Invoice System**: The invoicing system tracks each customer’s purchases, linking them to specific tracks.


Schema- Music Store Database  
![image](https://github.com/user-attachments/assets/8a8cf9f2-b7fe-4607-9784-34793c38b464)

