# Auth
There are many ways to protect our api. We'll be using json web tokens (JWT). JWT is an open standard that is heavily used. Because we're using a token approach, we don't need to keep track of who is signed in with a session store or have cookies. The JWT will be sent on every request because REST is stateless and we know not of the previous request. The token has to be stored on the client that is requesting resources
var user = {_id: '2873273237328378273'};

// send token back to client on signup/signin
var token = jwt.sign(user, 'shhhh, its a secret');

//...
// later on an incoming request, we will decode the token
// to see who the user is. The token is probably on the
// authorization header. This will throw an error if the token
// is not a valid JWT and instead is a random string.
var user = jwt.verify(req.headers.authorization, 'shhhh, its a secret');

// proceed to look user up to see if they exist in our system
User.findById(user._id, function(){});