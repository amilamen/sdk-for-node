const sdk = require('node-appwrite');

// Init SDK
let client = new sdk.Client();
client.addHeader('Origin', 'http://localhost');

let auth = new sdk.Auth(client);

client
	.setProject('project_id')
	.setKey('API_KEY')
;

let promise = auth.register(
    'emailx@example.com',
    'password',
    'https://localhost/confirm',
    'https://localhost/success',
    'https://localhost/failure',
    'my_name'
);

promise.then(function (response) {
	console.log(response);
}, function (error) {
	console.log(error);
});
