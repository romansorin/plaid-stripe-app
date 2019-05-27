### Plaid-Stripe integration

[Plaid Docs](https://plaid.com/docs/stripe/)
[Stripe Docs](https://stripe.com/docs/ach#using-plaid)

[Plaid Keys](https://dashboard.plaid.com/account/keys)
[Stripe Docs](https://dashboard.stripe.com/developers)

``` bash
# Unzip or upload the files found in plaid-stripe.zip
cd plaid-stripe
npm install
```

``` node
/* Go to index.js, run through comments and find what you want to configure.
   During production, store this in a more secure .env file or some kind of configuration file */
var APP_PORT = 8000;
var PLAID_CLIENT_ID = '5ce969b71186c3001245fb73'; // Public client id key
var PLAID_SECRET = 'b81f18309baf5d3bc4a446c6d56e9c'; // This key comes from 'sandbox', 'development', or 'production' secret
var PLAID_PUBLIC_KEY = 'af86fdcd156cb43e35a8cd9261333f'; // Public key
var PLAID_ENV = 'sandbox'; // 'sandbox', 'development', or 'production' - change as needed

var STRIPE_SECRET_KEY = 'sk_test_7wZvNlCbXQ62yDdUsIpVDVYO'; // This is your secret key for stripe. Currently, it is in test (demo) mode, so change it to live when you're ready
const stripe = require('stripe')(STRIPE_SECRET_KEY);

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

``` bash
# If running or testing locally, type in console:
node index.js
# Go to http://localhost:8000

# Otherwise, see how your hosting provider handles Node.JS apps. You'll need to edit the HTML in the EJS file and CSS for styling to fit your use case, but the logic is all there.
```

#### If you have any questions, feel free to email me at roman@romansorin.com. If needed in the future, I provide hosting services, design, and website/software development at romansorin.com
