# Basic implementation
```javascript
const clientId = 'your-client-id';  
const clientSecret = 'your-client-secret';  
const authorizationCode = 'authorization-code-from-step-2';  
const redirectUri = 'your-redirect-uri';  
const tokenEndpoint = 'authorization-server-token-endpoint';  
  
const tokenParams = new URLSearchParams();  
tokenParams.append('grant_type', 'authorization_code');  
tokenParams.append('code', authorizationCode);  
tokenParams.append('redirect_uri', redirectUri);  
tokenParams.append('client_id', clientId);  
tokenParams.append('client_secret', clientSecret);  
  
fetch(tokenEndpoint, {  
method: 'POST',  
body: tokenParams,  
})  
.then(response => response.json())  
.then(data => {  
const accessToken = data.access_token;  
// Now you have the access token to make requests!  
})  
.catch(error => {  
console.error('Error exchanging authorization code:', error);  
});
```

## Accessing protected resources
```javascript
const apiEndpoint = 'resource-server-api-endpoint';  
const headers = {  
Authorization: `Bearer ${accessToken}`,  
};  
  
fetch(apiEndpoint, {  
headers: headers,  
})  
.then(response => response.json())  
.then(data => {  
// Handle the fetched data from the resource server  
})  
.catch(error => {  
console.error('Error fetching protected resources:', error);  
});
```

