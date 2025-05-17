<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CyberScore</title>
</head>
<body>
  <h1>Dobrodošao na CyberScore!</h1>
  <div id="user-info">Nisi prijavljen</div>
  <br />
  <button onclick="login()">Prijavi se</button>
  <button onclick="logout()">Odjavi se</button>

  <script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
  <script>
    netlifyIdentity.init();

    // Kada se korisnik prijavi
    netlifyIdentity.on("login", user => {
      document.getElementById("user-info").innerText = `Ulogovan kao: ${user.email}`;
      netlifyIdentity.close();
    });

    // Kada se korisnik odjavi
    netlifyIdentity.on("logout", () => {
      document.getElementById("user-info").innerText = "Nisi prijavljen";
    });

    function login() {
      netlifyIdentity.open();
    }

    function logout() {
      netlifyIdentity.logout();
    }
  </script>
</body>
</html>
