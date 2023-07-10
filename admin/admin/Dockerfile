
FROM node:14-alpine

# Définir le répertoire de travail
WORKDIR /app

# Copier le package.json et le package-lock.json dans le répertoire de travail
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Copier tout le reste dans le répertoire de travail
COPY . .

# Définir les variables d'environnement pour l'application

ENV NODE_ENV=production
EXPOSE 4000

# Démarrer l'application
CMD ["npm", "start"
