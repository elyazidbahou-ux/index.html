[Untitled-1.html](https://github.com/user-attachments/files/24417622/Untitled-1.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Réclamation Biomédicale - CHU</title>

<style>
:root {
  --primary: #0b5ed7;
  --secondary: #f8f9fa;
  --danger: #dc3545;
  --warning: #fd7e14;
  --success: #198754;
  --border: #dee2e6;
}

body {
  font-family: "Segoe UI", Arial, sans-serif;
  background-color: #f4f6f9;
  margin: 0;
  padding: 20px;
}

.container {
  max-width: 900px;
  margin: auto;
}

h1 {
  text-align: center;
  color: var(--primary);
  margin-bottom: 30px;
}

.card {
  background: #ffffff;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 20px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.05);
  border-left: 5px solid var(--primary);
}

.card h2 {
  font-size: 18px;
  margin-bottom: 15px;
  color: var(--primary);
}

label {
  font-weight: 600;
  margin-top: 10px;
  display: block;
}

input, select, textarea {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  border: 1px solid var(--border);
  border-radius: 5px;
  font-size: 14px;
}

textarea {
  resize: vertical;
}

.checkbox-group,
.radio-group {
  margin-top: 10px;
}

.checkbox-group label,
.radio-group label {
  font-weight: normal;
  display: block;
  margin-bottom: 5px;
}

.urgent {
  color: var(--danger);
  font-weight: bold;
}

.warning {
  color: var(--warning);
}

.success {
  color: var(--success);
}

button {
  width: 100%;
  background-color: var(--primary);
  color: white;
  padding: 14px;
  font-size: 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  margin-top: 20px;
}

button:hover {
  background-color: #084298;
}

.footer-note {
  text-align: center;
  font-size: 12px;
  color: #6c757d;
  margin-top: 20px;
}
</style>
</head>

<body>
<div class="container">

<h1>FORMULAIRE DE RÉCLAMATION BIOMÉDICALE – CHU</h1>

<form action="/submit" method="post" enctype="multipart/form-data">

<!-- Informations générales -->
<div class="card">
<h2>🟦 Informations générales</h2>

<label>Service demandeur</label>
<select name="service" required>
  <option value="">Sélectionnez</option>
  <option>Urgences</option>
  <option>Réanimation</option>
  <option>Bloc opératoire</option>
  <option>Imagerie médicale</option>
  <option>Hospitalisation</option>
  <option>Consultations externes</option>
  <option>Laboratoire</option>
  <option>Autre</option>
</select>

<input type="text" name="autre_service" placeholder="Précisez le service" style="display:none;">

<label>Bâtiment / Pôle</label>
<input type="text" name="batiment" required>

<label>Étage / Local / Salle</label>
<input type="text" name="etage" required>
</div>

<!-- Identification équipement -->
<div class="card">
<h2>🟦 Identification de l’équipement</h2>

<label>Désignation de l’équipement</label>
<input type="text" name="designation" placeholder="Ex : Moniteur multiparamétrique" required>

<label>Famille biomédicale</label>
<select name="famille" required>
  <option value="">Sélectionnez</option>
  <option>Réanimation</option>
  <option>Imagerie médicale</option>
  <option>Bloc opératoire</option>
  <option>Diagnostic</option>
  <option>Thérapeutique</option>
  <option>Mobilier hospitalier</option>
  <option>Stérilisation</option>
  <option>Autre</option>
</select>

<label>Code inventaire biomédical</label>
<input type="text" name="code_inventaire" required>

<label>Numéro de série (si disponible)</label>
<input type="text" name="numero_serie">
</div>

<!-- Description panne -->
<div class="card">
<h2>🟦 Description de la panne</h2>

<div class="checkbox-group">
<label><input type="checkbox" name="type[]" value="Panne totale"> Panne totale</label>
<label><input type="checkbox" name="type[]" value="Dysfonctionnement partiel"> Dysfonctionnement partiel</label>
<label><input type="checkbox" name="type[]" value="Alarme / message d’erreur"> Alarme / message d’erreur</label>
<label><input type="checkbox" name="type[]" value="Problème logiciel"> Problème logiciel</label>
<label><input type="checkbox" name="type[]" value="Problème électrique"> Problème électrique</label>
<label><input type="checkbox" name="type[]" value="Autre"> Autre</label>
</div>

<label>Description détaillée</label>
<textarea name="description" rows="4" required></textarea>
</div>

<!-- Urgence -->
<div class="card">
<h2>🟦 Niveau d’urgence</h2>

<div class="radio-group">
<label class="urgent">
<input type="radio" name="urgence" value="Critique" required>
🔴 Critique – Impact direct sur le patient / arrêt de service
</label>

<label class="warning">
<input type="radio" name="urgence" value="Urgent">
🟠 Urgent – Risque à court terme
</label>

<label class="success">
<input type="radio" name="urgence" value="Normal">
🟢 Normal – Fonctionnement partiel
</label>
</div>
</div>

<!-- Pièces jointes -->
<div class="card">
<h2>🟦 Pièces jointes</h2>
<label>Photo ou vidéo (facultatif)</label>
<input type="file" name="fichier" accept="image/*,video/*">
</div>

<!-- Déclarant -->
<div class="card">
<h2>🟦 Informations du déclarant</h2>

<label>Nom et prénom</label>
<input type="text" name="nom" required>

<label>Fonction</label>
<input type="text" name="fonction" required>

<label>Téléphone</label>
<input type="tel" name="telephone" required>

<label>Date et heure</label>
<input type="datetime-local" name="date_heure" required>
</div>

<!-- Validation -->
<div class="card">
<label>
<input type="checkbox" name="confirmation" required>
Je confirme l’exactitude des informations fournies.
</label>
</div>

<button type="submit">📨 Soumettre la réclamation</button>

</form>

<p class="footer-note">
Service Biomédical – CHU | Plateforme de réclamation de maintenance
</p>

</div>

<button type="submit">📨 Soumettre la réclamation</button>

<!-- Bouton WhatsApp -->
<div style="margin-top:15px; text-align:center;">
  <a href="https://wa.me/2126XXXXXXXX?text=Nouvelle%20réclamation%20biomédicale%20soumise"
     target="_blank"
     style="
       display:inline-block;
       background:#25D366;
       color:white;
       padding:12px 20px;
       border-radius:6px;
       text-decoration:none;
       font-weight:bold;">
     📱 Notifier le service biomédical via WhatsApp
  </a>
</div>

<script>
document.querySelector('select[name="service"]').addEventListener('change', function () {
  document.querySelector('input[name="autre_service"]').style.display =
    this.value === 'Autre' ? 'block' : 'none';
});
</script>

</body>
</html>
