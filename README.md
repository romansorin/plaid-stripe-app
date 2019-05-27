# Plaid-Stripe integration

#### Stripe resources

[Stripe Docs](https://stripe.com/docs/ach#using-plaid),
[Stripe Keys](https://dashboard.stripe.com/developers)

#### Plaid resources

[Plaid Docs](https://plaid.com/docs/stripe/),
[Plaid Keys](https://dashboard.plaid.com/account/keys)

---

## Configuration

`.env`

```bash
git clone https://github.com/romansorin/plaid-stripe-app.git
cd plaid-stripe-app

# Install all necessary dependencies, these can be found in package.json
npm install
```

`index.js`

```js
/* Create a .env (dotenv) file in the root directory (i.e., where you find index.js) and configure the following variables. These ensure your keys are secure and never shared in commits: */

APP_PORT = 3000;
PLAID_CLIENT_ID = "yourCID";
PLAID_SECRET = "yourSecretEnvironment";
PLAID_PUBLIC_KEY = "yourPK";
PLAID_ENV = "yourEnv"; // Choose between sandbox, development, and production

STRIPE_SECRET_KEY = "yourSK"; // Use this variable regardless of using "test" or "production" API keys.
```

```js

/* You'll also want to take a look at the method for creating Stripe customers, and configure
   as needed.
   --------------
   This is just a sample method which successfully creates a customer
   You can modify the fields which are stored automatically, refer to https://stripe.com/docs/api/customers/object
*/
   stripe.customers.create({
        description: 'Customer created using Stripe + Plaid integration', // Change when you're ready
        // name: 'John Doe',
        // email: 'test@test.com',
        source: bankAccountToken // obtained with Stripe.js
      }, function (err, customer) {
        // async call
      });
/*
------------
Next take a look at views/index.ejs and find the following code segment, configure as needed:
*/
env: 'sandbox', // Change to 'production' when it is live on your site
clientName: 'Stripe + Plaid Test', // Change this to "Hunt Media" or whatever you want
key: 'af86fdcd156cb43e35a8cd9261333f' // This is your Plaid PUBLIC KEY
```

```bash
# If running or testing locally, type in console:
node index.js
# Go to http://localhost:8000

# Otherwise, see how your hosting provider handles Node.JS apps. You'll need to edit the HTML in the EJS file and CSS for styling to fit your use case, but the logic is all there.
```

#### If you have any questions, feel free to email me at roman@romansorin.com. If needed in the future, I provide hosting services, design, and website/software development at romansorin.com
