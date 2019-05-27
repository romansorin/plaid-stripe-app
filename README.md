# Plaid-Stripe integration

#### Stripe resources

[Stripe Docs](https://stripe.com/docs/ach#using-plaid),
[Stripe Keys](https://dashboard.stripe.com/developers)

#### Plaid resources

[Plaid Docs](https://plaid.com/docs/stripe/),
[Plaid Keys](https://dashboard.plaid.com/account/keys)

---

## Configuration

### Setup

```bash
git clone https://github.com/romansorin/plaid-stripe-app.git
cd plaid-stripe-app

# Install all necessary dependencies, these can be found in package.json
npm install
```

`.env`

```js
/* Create a .env (dotenv) file in the root directory (i.e., where you find index.js) and configure the following variables. These ensure your keys are secure and never shared in commits: */

APP_PORT = 3000;
PLAID_CLIENT_ID = "yourCID";
PLAID_SECRET = "yourSecretEnvironment";
PLAID_PUBLIC_KEY = "yourPK";
PLAID_ENV = "yourEnv"; // Choose between sandbox, development, and production

STRIPE_SECRET_KEY = "yourSK"; // Use this variable regardless of using "test" or "production" API keys.
```

`index.js`

```js
/* You'll also want to take a look at the method for creating Stripe customers, and configure
   as needed.
   --------------
   This is just a sample method which successfully creates a customer
   You can modify the fields which are stored automatically, refer to https://stripe.com/docs/api/customers/object
*/
stripe.customers.create({
  // ...
});
```

`views/index.ejs`

```js
/* Next, configure as needed:
*/
env: 'sandbox', // sandbox, development, production
clientName: 'Stripe + Plaid Test', // Change this to whatever you want
key: 'yourPublicKey' // This is your Plaid PUBLIC KEY
```

### Terminal:

```bash
# If running or testing locally, type in console:
node index.js

# Go to http://localhost:[APP_PORT]

# Otherwise, see how your hosting provider handles Node.JS apps.
```

#### If you have any questions, feel free to email me at roman@romansorin.com. If needed in the future, I provide hosting services, design, and website/software development at romansorin.com
