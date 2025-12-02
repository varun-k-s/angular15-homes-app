# Housing Listings — Angular 15 Learning Project

This is a learning project built using Angular 15, demonstrating a simple real-estate listings application with routing, components, interfaces, services, data fetching, and filtering functionality. The goal was to practice core Angular concepts in a structured, real example.

## Learning Source & Credit

This project was created while following the official Angular YouTube tutorial series:

Learning Angular playlist by the Angular team  
https://www.youtube.com/playlist?list=PL1w1q3fL4pmj9k1FrJ3Pe91EPub2_h4jF

---

# Features

✔ Home view showing all housing listings  
✔ Child component for individual listing cards  
✔ Details page for a specific listing using dynamic route parameters  
✔ Search filtering functionality  
✔ Angular service to fetch remote data (hosted using JSON-server here) 
✔ Works with a separate JSON server as mock backend API  
✔ Client-side rendering with data binding and directives  

---

# Project Architecture & Angular Concepts Used

## 🔹 Components Used

### `HomeComponent`
- Displays the main search bar and housing listings
- Uses *ngFor structural directive to loop over listing cards

### `HousingLocationComponent`
- Child component  
- Displays a single housing listing card  
- Receives data using @Input decorator:
    @Input() housingLocation!: HousingLocation;

### `DetailsComponent`
- Displays information of a specific housing listing
- Uses Angular routing & ActivatedRoute service to get route parameter:
    this.route.snapshot.params["id"]

---

## 🔹 Service Used

### `HousingService`
- Central service for fetching data from backend  
- Uses fetch() to get data from JSON server API:
    async getAllHousingLocations(): Promise<HousingLocation[]> {
      const data = await fetch(this.url);
      return await data.json();
    }

- Demonstrates Angular dependency injection:
    housingService: HousingService = inject(HousingService);

---

## 🔹 TypeScript Interface

### `HousingLocation`
Strongly types the housing objects:
    export interface HousingLocation {
      id: number;
      name: string;
      city: string;
      state: string;
      photo: string;
      availableUnits: number;
      wifi: boolean;
      laundry: boolean;
    }

---

## 🔹 Angular Routing

- Uses route parameter:  
    /details/:id

- Uses routerLink instead of href:  
    <a [routerLink]="['/details', housingLocation.id]">View Details</a>

This avoids full page reloads.

---

# Running the Project Locally

## Prerequisites
- Node.js installed

---

## Step 1: Clone this repository

    git clone <YOUR_REPO_URL>

Then open the project:

    cd <project-folder>

---

## Step 2: Install dependencies

    npm install

---

## Step 3: Start Angular server

    ng serve

App runs by default at:

    http://localhost:4200

---

## Step 4: Start JSON server for housing list json

    json-server --watch db.json

This runs by default at:

    http://localhost:3000/locations

---

# Some of the concepts in Angular being used in this project are:

Understanding Angular component structure
Using services & dependency injection  
Understanding Angular routing & route parameters  

---
