# api

**Description**
- Projet Spring Boot (API) qui gère des employés avec Spring Data JPA et MySQL.

**Prérequis**
- Java 21
- Maven
- MySQL (serveur) en cours d'exécution


**Créer la base MySQL (exemples)**

```sql
-- se connecter en root ou via sudo mysql
CREATE DATABASE api_db;
CREATE USER 'admin'@'localhost' IDENTIFIED BY '****';
GRANT ALL PRIVILEGES ON api_db.* TO 'admin'@'localhost';
FLUSH PRIVILEGES;
```

**Commandes utiles**

- Compiler et exécuter les tests :
```bash
mvn clean install
```

- Compiler sans lancer les tests :
```bash
mvn clean install -DskipTests
```

- Lancer l'application en développement :
```bash
mvn spring-boot:run
```

- Lancer le jar produit :
```bash
java -jar target/api-0.0.1-SNAPSHOT.jar
```

**Endpoints principaux**
- `GET /employee` : liste tous les employés
- `GET /employee/{id}` : récupère un employé par id
- `POST /employee` : crée un employé (body JSON)
- `PUT /employee/{id}` : met à jour un employé
- `DELETE /employee/{id}` : supprime un employé

**Exemples curl**
- Lister tous les employés :
```bash
curl -s http://localhost:9000/employee
```
- Récupérer un employé par id (ex id=1) :
```bash
curl -s http://localhost:9000/employee/1
```
- Créer un employé :
```bash
curl -s -X POST http://localhost:9000/employee \
	-H "Content-Type: application/json" \
	-d '{"firstName":"Paul","lastName":"DUPONT","mail":"paul@example.com","password":"secret"}'
```
- Mettre à jour un employé (ex id=1) :
```bash
curl -s -X PUT http://localhost:9000/employee/1 \
	-H "Content-Type: application/json" \
	-d '{"firstName":"Paul","lastName":"DUPONT","mail":"paul2@example.com","password":"newpass"}'
```
- Supprimer un employé (ex id=1) :
```bash
curl -s -X DELETE http://localhost:9000/employee/1
```

**Tests**
- Les tests utilisent la même configuration MySQL (si tu préfères isolation, tu peux ajouter H2 pour `src/test/resources/application.properties`).
- Commande courante : `mvn test` ou `mvn clean install`.

