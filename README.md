# PetCare - Veterinary Clinic Management System

A web application designed to streamline veterinary clinic operations by managing consultations, appointments, and patient records. Built as a university project to demonstrate full-stack development skills with ASP.NET Core MVC.

## About

PetCare is a comprehensive management system for veterinary clinics that handles the entire consultation workflow from appointment booking to final diagnosis. The system serves three different user types (pet owners, veterinarians, and administrator), each with their own dedicated interface and functionalities.

Think of it as a digital assistant for vet clinics, owners can book appointments online, vets can manage their schedule and record diagnoses and admin get insights into clinic operations through visual dashboards.

## Features

### For Pet Owners
- **Book Consultations** - Schedule appointments for your pets with just a few clicks
- **View Pets** - Manage your registered pets and their information
- **Consultation History** - Check past consultations and medical records

### For Veterinarians
- **Appointment Management** - View pending appointments and confirm them
- **Perform Consultations** - Record diagnoses, add treatment notes, and select procedures performed
- **Patient History** - Access complete medical history of any animal
- **Search Functionality** - Quickly find consultations by animal ID

### For Administrator
- **Analytics Dashboard** - Visual insights into clinic operations with three key charts:
  - Consultations per quarter (track seasonal trends)
  - Most performed treatments (identify popular procedures)
  - Most consulted species (understand patient demographics)
- **Year Filter** - Analyze data for any specific year

## Tech Stack

- **Backend:** ASP.NET Core 9.0 (MVC)
- **Database:** Entity Framework Core with SQL Server
- **Frontend:** Razor Views, Bootstrap 5, Chart.js
- **API:** RESTful API endpoints for data operations
- **Development:** Visual Studio 2022

##  Installation

### Prerequisites
- .NET 9.0 SDK
- Visual Studio 2022 (or Visual Studio Code)
- SQL Server (LocalDB or Express)

### Main NuGet Packages
- **Microsoft.EntityFrameworkCore** - ORM for database operations
- **Microsoft.EntityFrameworkCore.SqlServer** - SQL Server database provider
- **Microsoft.EntityFrameworkCore.Tools** - EF Core tools for migrations

### Steps

1. **Restore dependencies**
   ```bash
   dotnet restore
   ```

2. **Update database connection string** (if needed)
   
   Open `appsettings.json` and modify the connection string:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=PetCareDb;Trusted_Connection=True;"
   }
   ```

3. **Run the application**
   ```bash
   dotnet run
   ```
   
   Or press `F5` in Visual Studio

4. **Access the application**
   
   Open your browser and go to: `https://localhost:XXXX` (check console for exact port)

## Usage

### Default Test Accounts

The system comes with pre-seeded data for testing:

**Pet Owners:**
- Email: `joao@email.com` / Password: `123`
- Email: `ana@email.com` / Password: `123`

**Veterinarian:**
- Email: `vet@email.com` / Password: `123`

**Administrator:**
- Email: `admin@email.com` / Password: `admin`

### Typical Workflow

1. **Owner books consultation** → Status: "Pendente" (Pending)
2. **Vet confirms appointment** → Status: "Confirmada" (Confirmed)
3. **Vet performs consultation** → Adds diagnosis and procedures → Status: "Realizada" (Completed)
4. **Admin views analytics** → Dashboard updates with new data

## API Endpoints

The application includes a REST API for all data operations. Here are the main endpoints:

### Consultations
- `GET /api/data/consultations` - Get all consultations
- `POST /api/data/consultation` - Create new consultation
- `PUT /api/data/consultations/{id}/confirm` - Confirm consultation
- `POST /api/data/consultations/finalize` - Complete consultation with diagnosis

### Users
- `GET /api/data/owners` - Get all pet owners
- `GET /api/data/veterinarian` - Get all veterinarians

### Animals
- `GET /api/data/animals/owner/{ownerId}` - Get pets by owner

### Procedures
- `GET /api/data/procedures` - Get all available treatments

## 📊 Database Schema

Main entities and relationships:
- **Users** (Owners, Vets, Admins)
- **Animals** (belongs to Owner)
- **Consultations** (links Animal, Owner, and Vet)
- **VeterinaryProcedures** (available treatments)
- **PerformedProcedures** (treatments done in each consultation)


## Future Improvements

Based on some feedback and best practices:

- **Separate API Project** - Extract API into standalone project for better architecture
- **Split Controllers** - Divide `DataController` into separate controllers (Users, Animals, Consultations, Procedures)
- **Authentication System** - Implement proper authentication with JWT tokens
- **Email Notifications** - Send confirmation emails to owners
- **Mobile App** - Create mobile version using the same API
- **Payment Integration** - Add online payment for consultations
- **Appointment Reminders** - Automated SMS/email reminders
- **Medical Records Upload** - Allow file attachments (X-rays, lab results)

## Author

Created as a university project to demonstrate full-stack web development skills.

**Academic Context:**
- Institution: Beja Polytechnic Institute (IPBeja)
- Year: 2025/2026

**Note:** This project was developed for educational purposes. In a production environment, proper security measures, error handling, and testing would be essential.
