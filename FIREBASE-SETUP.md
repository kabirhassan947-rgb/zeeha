# Switch on customer accounts (about 10 minutes)

Customers can sign up, log in, save their delivery details and see their orders. Accounts stay switched off until you finish these steps, and shopping works normally without them. Firebase is free for a small shop.

1. Go to console.firebase.google.com and sign in with a Google account. Click **Create a project**, name it `zeeha`, and you can turn Google Analytics off.
2. In the left menu open **Build > Authentication**, click **Get started**, choose **Email/Password**, switch on the first toggle, and **Save**.
3. Still in Authentication, open **Settings > Authorized domains**, click **Add domain**, and add `kabirhassan947-rgb.github.io`.
4. Open **Build > Firestore Database**, click **Create database**, pick the closest location, and choose **Start in production mode**.
5. In Firestore, open the **Rules** tab, delete everything there, paste the rules below, and click **Publish**.
6. Click the gear icon next to **Project Overview**, then **Project settings**. Under **Your apps** click the **</>** (web) icon, name the app `zeeha`, and click **Register app**. Copy the block that starts with `const firebaseConfig = {` ... `};`.
7. Open your `admin.html` page and paste that block into **Customer accounts**. Click **Download products.json**, then upload it to GitHub (**Add file > Upload files**) and commit. A **Log in** button appears on your shop within a couple of minutes.

## Rules to paste in step 5

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
    match /orders/{id} {
      allow create: if request.auth != null && request.resource.data.uid == request.auth.uid;
      allow read: if request.auth != null && resource.data.uid == request.auth.uid;
    }
  }
}
```

## Seeing your customers' orders

Open the Firebase console, then **Firestore Database > Data > orders**. Every order from a logged-in customer is listed there with their name, phone, address, items and total. Orders from customers who are not logged in do not appear there, so keep using your Paystack dashboard and WhatsApp for those. Customers see their own orders only.

## Important

The order record is created in the customer's browser. Always check the amount in your Paystack dashboard before shipping, and treat the order list as a record, not as proof of payment.
