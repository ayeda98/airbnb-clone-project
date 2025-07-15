Airbnb Clone Project
I. Project Initialization
🎯 Project Goal
The objective of this project is to replicate the core features of the Airbnb website, focusing on both backend functionality and essential user interactions.
<ul>
✅ Key Features
	•	<ol>🏠 Create and book listings</ol>
	•	<ol>👤 User authentication and management</ol>
	•	<ol>📍 Listing management: title, description, price, location, images, etc.</ol>
	•	<ol>📅 Booking system with calendar integration</ol>
	•	<ol>💬 Ratings and comments system</ol>
	•	<ol>💳 Online payment integration (Stripe, PayPal, etc.)</ol>
	•	<ol>🔐 Security, input validation, and error handling</ol>
</ul>

II. Team Roles
<table>
  <thead>
    <tr>
      <th>👤 Rôle</th>
      <th>📌 Responsabilités</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Project Manager</td>
      <td>Coordination, suivi du planning, gestion des tâches</td>
    </tr>
    <tr>
      <td>Backend Developer</td>
      <td>Création des APIs, logique métier, sécurité, validation</td>
    </tr>
    <tr>
      <td>Frontend Developer</td>
      <td>Interface utilisateur, intégration API, design responsive</td>
    </tr>
    <tr>
      <td>Database Administrator</td>
      <td>Modélisation de la base, optimisation, migrations</td>
    </tr>
    <tr>
      <td>QA Engineer</td>
      <td>Tests (fonctionnels, unitaires), rapport de bugs</td>
    </tr>
    <tr>
      <td>DevOps Engineer</td>
      <td>Déploiement, CI/CD, supervision des environnements</td>
    </tr>
  </tbody>
</table>

III. Technology Stack
<table>
  <thead>
    <tr>
      <th>🧩 Composant</th>
      <th>⚙️ Technologies utilisées</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Backend</td>
      <td>Django, Django REST Framework</td>
    </tr>
    <tr>
      <td>Base de données</td>
      <td>MySQL</td>
    </tr>
    <tr>
      <td>Authentification</td>
      <td>Django Auth, JWT (simplejwt)</td>
    </tr>
    <tr>
      <td>API</td>
      <td>REST (DRF)</td>
    </tr>
    <tr>
      <td>Paiement</td>
      <td>Stripe, PayPal</td>
    </tr>
    <tr>
      <td>Déploiement</td>
      <td>pythonanywhere</td>
    </tr>
  </tbody>
</table>


IV. Database Design

<ul>
<li><h1>User</h1></li>
<table>
  <thead>
    <tr>
      <th>Champ</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td>Integer</td>
      <td>Identifiant unique de l’utilisateur</td>
    </tr>
    <tr>
      <td><code>email</code></td>
      <td>String</td>
      <td>Adresse email (unique)</td>
    </tr>
    <tr>
      <td><code>is_host</code></td>
      <td>Boolean</td>
      <td>Indique si l’utilisateur est un hôte</td>
    </tr>
  </tbody>
</table>
<li><h1>Property</h1></li>

<table>
  <thead>
    <tr>
      <th>Champ</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td>Integer</td>
      <td>Identifiant du logement</td>
    </tr>
    <tr>
      <td><code>owner_id</code></td>
      <td>FK(User)</td>
      <td>Référence vers le propriétaire</td>
    </tr>
    <tr>
      <td><code>price_per_night</code></td>
      <td>Decimal</td>
      <td>Prix par nuit</td>
    </tr>
  </tbody>
</table>

<li><h1>Booking</h1></li>
<table>
  <thead>
    <tr>
      <th>Champ</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td>Integer</td>
      <td>Identifiant de la réservation</td>
    </tr>
    <tr>
      <td><code>user_id</code></td>
      <td>FK(User)</td>
      <td>Utilisateur ayant réservé</td>
    </tr>
    <tr>
      <td><code>start_date</code></td>
      <td>Date</td>
      <td>Date d’arrivée</td>
    </tr>
  </tbody>
</table>

<li><h1>Review</h1></li>
<table>
  <thead>
    <tr>
      <th>Champ</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td>Integer</td>
      <td>Identifiant du commentaire</td>
    </tr>
    <tr>
      <td><code>rating</code></td>
      <td>Integer</td>
      <td>Note sur 5</td>
    </tr>
    <tr>
      <td><code>property_id</code></td>
      <td>FK(Property)</td>
      <td>Logement concerné</td>
    </tr>
  </tbody>
</table>


<li><h1>Payment</h1></li>
<table>
  <thead>
    <tr>
      <th>Champ</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td>Integer</td>
      <td>Identifiant du paiement</td>
    </tr>
    <tr>
      <td><code>amount</code></td>
      <td>Decimal</td>
      <td>Montant total payé</td>
    </tr>
    <tr>
      <td><code>status</code></td>
      <td>Enum</td>
      <td>État du paiement (paid, pending, failed)</td>
    </tr>
  </tbody>
</table>

</ul>

Feature Breakdown

## ✨ Feature Breakdown

### 👤 User Management
Users can register, log in, and manage their profiles. This feature enables personalized access and distinguishes between guests and hosts for proper access control.

### 🏘️ Property Management
Hosts can create, update, and delete property listings, including uploading photos, setting prices, and defining availability. This is essential for allowing users to browse and choose from various accommodation options.

### 📅 Booking System
Guests can check availability, book properties, and receive booking confirmations. This feature ensures that reservations are properly tracked and dates are managed.

### 💳 Payment Integration
Guests can pay for bookings via secure online payment methods such as Stripe or PayPal. It provides a safe transaction system that benefits both hosts and guests.

### ⭐ Review and Rating
Guests can leave feedback on properties after their stay, rating their experience. This helps build trust in the community and encourages quality hosting.

### 🔒 Authentication and Authorization
Users must be authenticated to perform specific actions like booking or listing properties. This prevents unauthorized access to protected resources.

### 🖼️ Image Upload
Hosts can upload multiple images per property, with one being marked as the cover. This improves the attractiveness and clarity of listings for potential guests.

API Security

To protect users and data, the project will implement the following security measures:

- **Authentication**: Only registered users can log in and perform actions. We'll use JWT tokens to maintain secure sessions.
- **Authorization**: Ensures that users can only access resources they are permitted to (e.g., a user cannot delete another user's listing).
- **Rate Limiting**: Prevents abuse of APIs by limiting the number of requests per user/IP.
- **Data Validation and Sanitization**: Inputs will be validated on both frontend and backend to avoid injection attacks.
- **Secure Payment Processing**: Payment APIs (like Stripe/PayPal) use encryption and fraud protection to ensure transaction safety.

Security is crucial to protect personal data, prevent fraud, and build user trust in the platform.

## ⚙️ CI/CD Pipeline

CI/CD (Continuous Integration and Continuous Deployment) helps automate the testing, building, and deployment process of the project.

- **Continuous Integration (CI)** ensures that every change to the codebase is automatically tested and validated.
- **Continuous Deployment (CD)** allows us to push changes to production or staging environments with minimal manual intervention.

We will use **GitHub Actions** for automating workflows such as testing and deployment. **Docker** may also be used to ensure consistent environments across development and production.
git add README.md
git commit -m "Add Feature Breakdown, API Security, and CI/CD sections"
git push origin main