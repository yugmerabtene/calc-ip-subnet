### **Cours sur le calcul d'adresses IP et de sous-réseaux**

#### **Introduction**
Dans un réseau, le sous-réseau permet de diviser une adresse IP en plusieurs blocs plus petits pour optimiser l’utilisation des adresses et segmenter le réseau. Chaque sous-réseau possède :
- Une adresse de réseau,
- Un masque de sous-réseau,
- Une plage d’adresses utilisables pour les hôtes,
- Une adresse de diffusion (broadcast).

Prenons un exemple avec l’adresse **172.16.0.0/28** (au lieu de l’adresse de la question) pour expliquer comment déterminer les éléments demandés.

---

### **1. Masque de sous-réseau en notation binaire**
Le masque de sous-réseau détermine la partie réseau et la partie hôte d'une adresse IP. Avec un préfixe `/28`, cela signifie que les 28 premiers bits représentent la partie réseau et les 4 derniers bits sont réservés pour les hôtes.

1. Écriture binaire d’une adresse IPv4 : une adresse est composée de 4 octets (32 bits).  
2. Les 28 bits pour le réseau seront tous à `1`, et les 4 bits restants à `0`.

   **Notation binaire du masque pour /28 :**  
   ```
   11111111.11111111.11111111.11110000
   ```
3. Convertissez chaque octet en notation décimale :  
   ```
   255.255.255.240
   ```

**Conclusion :** Le masque pour **/28** est **255.255.255.240**.

---

### **2. Nombre d’adresses IP utilisables**
Le nombre total d’adresses dans un sous-réseau est donné par la formule :  
\[
2^n
\]
où \( n \) est le nombre de bits disponibles pour les hôtes. Pour **/28**, il reste \( 32 - 28 = 4 \) bits pour les hôtes.

1. **Nombre total d’adresses IP dans le sous-réseau :**  
   \[
   2^4 = 16 \text{ adresses}
   \]
2. **Adresses réservées :**  
   - 1 pour l’adresse de réseau,  
   - 1 pour l’adresse de diffusion.  
   \[
   \text{Adresses utilisables : } 16 - 2 = 14 \text{ adresses.}
   \]

**Conclusion :** Ce sous-réseau peut attribuer **14 adresses IP** aux hôtes.

---

### **3. Adresse de diffusion (broadcast)**
L’adresse de diffusion est utilisée pour communiquer avec tous les appareils d’un sous-réseau.

**Étapes pour déterminer l’adresse de diffusion :**
1. Identifiez la plage d’adresses en fonction du masque.
   - **Adresse de réseau :** \( 172.16.0.0 \) (tous les bits hôtes à `0`).
   - **Adresse de diffusion :** \( 172.16.0.15 \) (tous les bits hôtes à `1` dans le dernier octet).
2. Écrivez les adresses en binaire pour vérifier :
   - Adresse réseau :  
     ```
     10101100.00010000.00000000.00000000
     ```
   - Adresse de diffusion :  
     ```
     10101100.00010000.00000000.00001111
     ```

**Conclusion :** L’adresse de diffusion est **172.16.0.15**.

---

### **4. Première adresse utilisable**
La première adresse utilisable est l’adresse immédiatement après l’adresse de réseau.

**Étapes :**
1. Prenez l’adresse réseau et ajoutez 1 au dernier bit.
   - Adresse réseau : \( 172.16.0.0 \)  
   - Première adresse utilisable : \( 172.16.0.1 \)
2. Vérifiez qu’elle ne correspond ni à l’adresse de réseau ni à l’adresse de diffusion.

**Conclusion :** La première adresse utilisable est **172.16.0.1**.

---

### **5. Synthèse avec l'exemple**
Pour l’adresse **172.16.0.0/28** :
- **Masque de sous-réseau :** 255.255.255.240  
- **Nombre d’adresses utilisables :** 14  
- **Adresse de diffusion :** 172.16.0.15  
- **Première adresse utilisable :** 172.16.0.1  

---

### **Exercice pratique**
1. Prenez l’adresse **10.0.0.0/27** et répétez les étapes ci-dessus pour identifier :  
   - Le masque de sous-réseau,  
   - Le nombre d’adresses utilisables,  
   - L’adresse de diffusion,  
   - La première adresse utilisable.  
2. Comparez vos réponses pour vous assurer que vous comprenez bien le raisonnement.

