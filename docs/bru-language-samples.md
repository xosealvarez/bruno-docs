# Samples

Here are a few sample Bru files.

## GET
```bash
get {
  url: https://api.github.com/users/usebruno
}
```

## GET with headers
```
get {
  url: https://api.textlocal.in/send?apiKey=secret&numbers=9988776655&message=hello
}

headers {
  content-type: application/json
  Authorization: Bearer topsecret
}
```

## POST with body
```
post {
  url: https://api.textlocal.in/send
}

body {
  {
    "apiKey": "secret",
    "numbers": "9988776655",
    "message": "Woof! lets play with some apis"
  }
}

headers {
  content-type: application/json
  Authorization: Bearer topsecret
}
```

## Scripting
```
post {
  url: https://api.textlocal.in/login
}

body {
  {
    "username": "johnnash",
    "password": "governingdynamics"
  }
}

script-post-response {
  bru.setVar("token", res.body.token);
}
```

## Testing
```
post {
  url: https://api.textlocal.in/login
}

body {
  {
    "username": "johnnash",
    "password": "governingdynamics"
  }
}

tests {
  test("should be able to login", function() {
    expect(res.status).to.equal(201);
  });
  
  test("should receive the token", function() {
    expect(res.body.token).to.be.a('string');
  });
}
```
