# Laboratoire-partitions-tables

# Documentation : Partitionnement d’un PC et Configuration BIOS/UEFI

## Matériel requis

- **PC du client (Boîtier “Rétablissement 4”)**
- **Kit “trio SSD”** (à utiliser pour le cours matériel)
- **Serveur d’image Aomei** pour le déploiement de l’image Windows 10

---

## PARTIE #1 : Configuration et Installation sur le PC du Client

### Étape 1 : Préparer le matériel
1. Localisez le boîtier **“Rétablissement 4”** sur les étagères derrière la classe.
2. À l’aide du **Kit trio SSD** (en votre possession), insérez le disque dur SSD de votre kit dans le compartiment 2,5’’ du boîtier **“Rétablissement 4”**. 
   - **Important :** Ne placez rien dans le compartiment marqué “ne pas utiliser”.
   
### Étape 2 : Démarrer en mode “Réseau”
3. Activez le démarrage **“Réseau”** sur la carte mère du PC. Cela permet de démarrer l’ordinateur depuis un disque dur sur un autre ordinateur, le **serveur d’image Aomei**. Ce serveur contient des images système à déployer.

### Étape 3 : Déployer l’image Windows 10
4. Suivez les instructions pour déployer une image système **“Win10 STD”** via le serveur Aomei. Cette image est disponible dans le répertoire **“Rétablissement”** sur le serveur d’image Aomei.
5. Une fois l’image installée, redémarrez l’ordinateur normalement.

---

## PARTIE #2 : Vérification du Mode BIOS/UEFI

### Méthode #1 : Utilisation de MSInfo32

1. **Ouvrir l'outil d’informations système (MSInfo32)** :
   - Appuyez simultanément sur les touches **“Windows” + R** pour ouvrir la boîte de dialogue **Exécuter**.
   - Tapez **msinfo32** et appuyez sur **Entrée**.

2. **Vérification du mode BIOS/UEFI** :
   - Une fenêtre **Informations système** s’ouvre.
   - Recherchez la ligne **“Mode BIOS”** :
     - Si la valeur est **UEFI**, l'ordinateur utilise un mode **UEFI**.
     - Si la valeur est **BIOS Legacy**, l'ordinateur utilise un mode **BIOS** traditionnel.

---

## PARTIE #3 : Vérification du Type de Partition (GPT ou MBR)

### Méthode #1 : Utilisation de la ligne de commande avec Diskpart

1. **Redémarrer l’ordinateur en mode de récupération** :
   - Maintenez la touche **Shift** enfoncée et cliquez sur l'icône **“Alimentation”** dans la barre des tâches.
   - Sélectionnez **“Redémarrer”**.
   
2. **Accéder à l’invite de commande** :
   - Une fois l’ordinateur redémarré, dans le menu **Options avancées**, sélectionnez **Dépannage > Options avancées > Invite de commande**.

3. **Lancer Diskpart** :
   - Tapez la commande suivante pour ouvrir l’utilitaire **diskpart** :
     ```
     diskpart
     ```
     Appuyez sur **Entrée**.

4. **Lister les disques disponibles** :
   - Tapez la commande suivante pour afficher la liste des disques connectés :
     ```
     list disk
     ```
     Cela affichera tous les disques présents sur votre ordinateur avec des informations comme la taille du disque et le type de partition (GPT ou MBR).

5. **Vérifier le type de partition (GPT ou MBR)** :
   - Dans la sortie de la commande `list disk`, regardez la colonne **GPT** :
     - Si un astérisque (*) apparaît sous la colonne GPT, cela signifie que le disque est en **GPT**.
     - Si l'astérisque n’est pas présent, le disque est en **MBR**.

### Méthode #2 : Utilisation du Gestionnaire de Disques Windows

1. **Accéder à la gestion des disques** :
   - Clic droit sur **Démarrer** puis sélectionnez **Gestion des disques**.
   
2. **Vérification du type de partition** :
   - Dans la fenêtre de gestion des disques, localisez le disque que vous souhaitez analyser.
   - Faites un clic droit sur le disque (pas sur la partition) et sélectionnez **Propriétés**.
   - Allez dans l’onglet **Volumes**. Le **Style de partition** sera mentionné, indiquant soit **MBR** (Master Boot Record), soit **GPT** (GUID Partition Table).

---

## Réponses aux Questions

1. **Nom de l'ordinateur** :
   - Allez dans **MSInfo32** et trouvez la ligne **“Nom de l’ordinateur”** pour répondre à cette question.

2. **Fabricant de la carte mère** :
   - Dans **MSInfo32**, sous la section **Fabricant de la carte mère**, vous trouverez le nom du fabricant.

3. **Modèle de la carte mère** :
   - Toujours dans **MSInfo32**, cherchez la ligne **Modèle de la carte mère** pour obtenir cette information.

4. **Mode BIOS de la carte mère** :
   - La ligne **Mode BIOS** dans **MSInfo32** vous indiquera si la carte mère fonctionne en **UEFI** ou en **BIOS Legacy**.

---

## Conclusion

Cette documentation vous guide à travers les étapes nécessaires pour configurer un PC du client, installer une image système, et vérifier les informations relatives au BIOS et au type de partition du disque. En suivant chaque méthode, vous pourrez facilement déterminer si l’ordinateur utilise un système UEFI ou un BIOS Legacy et si le disque est en GPT ou MBR.

Si vous avez des questions ou des doutes supplémentaires, n’hésitez pas à demander des éclaircissements ou de l’aide supplémentaire !
