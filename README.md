# Pet Care Management System

A decentralized pet care management system built on the Internet Computer platform using Azle. This system facilitates interactions between pet owners, veterinarians, and administrators while managing pet care services, appointments, and records.

## Features

- **User Management**

  - Multiple user roles (Pet Owner, Veterinarian, Admin)
  - User registration with validation
  - Profile management

- **Pet Management**

  - Pet registration and profiles
  - Pet adoption system
  - Pet ownership tracking

- **Veterinary Services**

  - Appointment scheduling
  - Health record management
  - Prescription management
  - Payment processing

- **Communication**
  - Messaging system between users
  - Notification system
  - Real-time updates

## Prerequisites

- Node.js (v16 or higher)
- DFX CLI (latest version)
- Git

## Installation

1. Clone the repository:

```bash
git clone https://github.com/devshillah/online-vet-care.git
cd online-vet-care
```

2. Install dependencies:

```bash
npm install
```

3. Start the local Internet Computer replica:

```bash
dfx start --background
```

4. Deploy the canister:

```bash
dfx deploy
```

## System Architecture

### Data Models

- **User**: Stores user information and role (PetOwner/Veterinarian/Admin)
- **Pet**: Contains pet details and ownership information
- **Appointment**: Manages veterinary appointments
- **HealthRecord**: Stores pet health records
- **Prescription**: Manages medical prescriptions
- **Message**: Handles communication between users
- **Notification**: Manages system notifications
- **Payment**: Processes and tracks payments
- **PetAdoption**: Manages pet adoption requests

### Core Functions

#### User Management

- `createUser`: Register new users with validation
- `getUsers`: Retrieve all registered users

#### Pet Management

- `addPet`: Register new pets
- `getPets`: Retrieve all registered pets
- `getUserPets`: Get pets belonging to a specific user

#### Appointment System

- `scheduleAppointment`: Book veterinary appointments
- `getAppointments`: Retrieve all appointments
- `getUserAppointments`: Get appointments for a specific user

#### Health Records

- `addHealthRecord`: Add new health records
- `getHealthRecords`: Retrieve all health records
- `getUserHealthRecords`: Get health records for a specific user

#### Prescriptions

- `addPrescription`: Create new prescriptions
- `getPrescriptions`: Retrieve all prescriptions

#### Communication

- `sendMessage`: Send messages between users
- `getMessages`: Retrieve messages
- `sendNotification`: Send system notifications
- `getNotifications`: Retrieve notifications

#### Payments

- `makePayment`: Process payments
- `getPayments`: Retrieve payment records

#### Adoption System

- `adoptPet`: Submit pet adoption requests
- `getPetAdoptions`: Retrieve adoption records

## Security Features

- Email validation
- Phone number validation
- Unique username enforcement
- Data validation for all inputs
- Error handling for all operations

## Error Handling

The system implements a comprehensive error handling system with specific error types:

- `NotFound`: When requested resources don't exist
- `InvalidPayload`: When input data is invalid
- `Unauthorized`: For authentication/authorization errors

## Usage Examples

### Creating a New User

```typescript
const userPayload = {
  username: "john_doe",
  email: "john@example.com",
  phoneNumber: "+1234567890",
  role: { PetOwner: null },
};

const result = await createUser(userPayload);
```

### Scheduling an Appointment

```typescript
const appointmentPayload = {
  petId: "pet-uuid",
  veterinarianId: "vet-uuid",
  date: "2024-03-15T10:00:00Z",
};

const result = await scheduleAppointment(appointmentPayload);
```

## Things to be explained in the course:

1. What is Ledger? More details here: https://internetcomputer.org/docs/current/developer-docs/integrations/ledger/
2. What is Internet Identity? More details here: https://internetcomputer.org/internet-identity
3. What is Principal, Identity, Address? https://internetcomputer.org/internet-identity | https://yumimarketplace.medium.com/whats-the-difference-between-principal-id-and-account-id-3c908afdc1f9
4. Canister-to-canister communication and how multi-canister development is done? https://medium.com/icp-league/explore-backend-multi-canister-development-on-ic-680064b06320

## How to deploy canisters implemented in the course

### Internet identity canister

`dfx deploy internet_identity` - that is the canister that handles the authentication flow. Once it's deployed, the `js-agent` library will be talking to it to register identities. There is UI that acts as a wallet where you can select existing identities
or create a new one.
