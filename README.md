# Broker Admin dashboard

The Broker Admin Panel is designed to manage users, transactions, wallet addresses, and user profile data. The app uses Firebase as its backend for real-time data storage and authentication. It is structured to ensure easy navigation and control over user data and administrative tasks, such as handling transaction records and updating wallet information.

## Project Structure

The project follows a modular structure, with each functional part of the admin panel contained in separate components. Here’s a high-level overview of key components and their roles:

* App.js: The root component handling the conditional display for the entire application. The components decide between the `<GetUser />` and the `<GetDash />` to display based on authentication case.

* GetUser.js: The component only displays when the user is not authenticated, it routes the `GetAuth.js`, `NotFound.js`, and `Download.js`.

* GetDash.js: The component only displays when the user is authenticated and holds route for the main aspect of the App like Dashboard, KYC, AllUsers, etc.

## Packages Used
* React: Core library for building the UI.
* React Router DOM: Used for routing and navigation within the app.
* Firebase: Backend service for real-time data, authentication, and Firestore database.
* CSS: Custom styles used to design the interface and layout.
* React Icons: Provides iconography for the user interface (for buttons, menus, etc.).
* See `package.json` for other dependencies.

## Dashboard Routing Configuration

The following routes are defined in the application:

```jsx
<div className='contents'>
  <Routes>
    <!-- Dashboard Route: Displays the dashboard component with the current user's UID -->
    <Route path="/" element={<Dashboard userId={user.uid} />} />

    <!-- Users Route: Displays the component with a list of all users -->
    <Route path="/users" element={<AllUsers />} />

    <!-- Download Route: Displays the download page -->
    <Route path="/download" element={<Download />} />

    <!-- User Detail Route: Displays the details for a specific user based on their ID -->
    <Route path="/users/:userId" element={<UserDetail />} />

    <!-- Add Transaction Route: Allows adding a transaction to the system -->
    <Route path="/add-transaction" element={<AddTransaction />} />

    <!-- Settings Route: Displays the settings page for updating configurations like wallets -->
    <Route path="/settings" element={<Settings />} />

    <!-- User Transactions Route: Displays the transaction logs for a specific user -->
    <Route path="/user/:userId/transactions" element={<TransactionLogs userId={user.uid} />} />

    <!-- KYC Route: Displays the KYC (Know Your Customer) details for a specific user -->
    <Route path="/kyc/:userId" element={<Kyc
        userName={profileData.fullName}
        profilePictureUrl={profileData.profilePictureUrl}
    />} />

    <!-- Not Found Route: Displays a custom 404 page for undefined routes -->
    <Route path="*" element={<NotFound />} />

    <!-- Logout Route: Displays the page when a user is logged out or unauthorized (not admin) -->
    <Route path="/logout" element={<NotAdmin
        userName={profileData.fullName}
        profilePictureUrl={profileData.profilePictureUrl}
    />} />
  </Routes>
</div>
```


## Styling
The project uses CSS and Bootstrap for custom styling, ensuring that the admin panel looks professional and is easy to navigate. The design includes responsive elements, ensuring the app works across different screen sizes, from mobile to desktop.

## Security
The admin panel ensures security in the following ways:

* Authentication and Role-Based Access Control: Only authenticated admins can access the dashboard and sensitive information. Firebase Authentication handles both login and role verification.
* Real-Time Data Validation: All updates (e.g., user data changes) are validated to prevent unauthorized modifications.

## Future Upgrades and Enhancements

### Two-Factor Authentication (2FA) for Admin Login
* Upgrade: Add two-factor authentication to enhance security for admin logins.
* Benefit: Strengthens security and reduces the risk of unauthorized access to the admin panel.

### API Integration for External Services
Enable Email notification for both users and admins based on each data actions, eg. Admin Upgraded User Plans.

### Batch User Actions
* Upgrade: Implement bulk actions for user management (e.g., suspend multiple users, approve multiple KYC requests).
* Benefit: Increases efficiency by allowing admins to manage multiple users simultaneously.

### Multi-Language Support
* Upgrade: Add support for multiple languages to make the admin panel accessible to international teams.
* Benefit: Increases the app's usability for a global audience.

### Audit Logs for Admin Actions
* Upgrade: Create an audit log that tracks actions performed by admin users (e.g., adding transactions, changing settings, etc.).
* Benefit: Improves transparency and accountability by providing a detailed history of admin actions.

### Advanced Analytics Dashboard
* Upgrade: Integrate advanced analytics and reporting tools to visualize key metrics like user activity, transaction volume, and system performance.
* Benefit: Provides admins with deeper insights into platform usage, helping with decision-making and optimization.


