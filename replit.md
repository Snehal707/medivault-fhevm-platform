# MediVault - Encrypted Health Records Platform

## Overview

MediVault is a blockchain-based health records management platform that leverages Zama's Fully Homomorphic Encryption (FHEVM) technology to enable secure computation on encrypted health data. The application allows users to store, manage, and selectively share their medical information while maintaining complete privacy through end-to-end encryption. Healthcare providers can access permitted data and perform analytics without ever seeing the raw, unencrypted information.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The client is built using React with TypeScript and modern tooling including Vite for development and building. The UI framework uses shadcn/ui components built on top of Radix UI primitives and styled with Tailwind CSS. The application follows a component-based architecture with a tabbed interface for different functional areas (Dashboard, Health Records, Access Control, Emergency, and FHEVM settings).

State management is handled through React Query (TanStack Query) for server state and React hooks for local state. The routing is implemented using Wouter, a lightweight React router. The application includes wallet connectivity for MetaMask integration to interact with blockchain networks.

### Backend Architecture
The server is built with Express.js and TypeScript, following a REST API pattern. The architecture separates concerns with distinct modules for routing, database access, and business logic. The server handles health record CRUD operations, access permission management, emergency contact information, and audit logging.

The storage layer is abstracted through an interface-based design pattern, allowing for different storage implementations. The current implementation uses a DatabaseStorage class that handles all database interactions through Drizzle ORM.

### Data Storage Solutions
The application uses PostgreSQL as the primary database with Drizzle ORM for type-safe database operations. The database schema includes tables for users, health records, access permissions, emergency contacts, emergency information, and audit logs. All sensitive health data is stored in encrypted form using FHEVM encryption before being persisted to the database.

Connection to the database is managed through Neon's serverless PostgreSQL adapter, which provides WebSocket-based connections suitable for serverless environments. Database migrations are handled through Drizzle Kit.

### Authentication and Authorization
User authentication is blockchain-based, using wallet addresses as unique identifiers. Users connect through MetaMask wallet integration, and their wallet address serves as their primary authentication credential. The system stores minimal user information, focusing on the wallet address and creation timestamp.

Access control is implemented through a permission-based system where users can grant specific healthcare providers access to certain types of their health data for defined time periods. The system includes audit logging to track all access attempts and data operations.

### External Service Integrations
The application integrates with MetaMask for wallet connectivity and blockchain interactions. The FHEVM integration with Zama's technology enables fully homomorphic encryption capabilities, allowing computations on encrypted health data without decryption.

The system is designed to work with various blockchain networks, with network detection and switching capabilities built into the wallet integration. Database connectivity is managed through Neon's serverless PostgreSQL service, providing scalable and reliable data storage.

## External Dependencies

- **Database**: PostgreSQL via Neon serverless
- **Blockchain Integration**: MetaMask wallet connectivity
- **Encryption**: Zama FHEVM for fully homomorphic encryption
- **UI Framework**: Radix UI primitives with shadcn/ui components
- **Styling**: Tailwind CSS with custom design system
- **State Management**: TanStack React Query for server state
- **Database ORM**: Drizzle ORM with type-safe schema definitions
- **Development Tools**: Vite for building and development server
- **Runtime**: Node.js with Express.js for the backend API