FROM node:14

# Définir le répertoire de travail
WORKDIR /usr/src/app

# Copier le package.json et le package-lock.json dans le répertoire de travail
COPY ["package.json", "package-lock.json", "npm-shrinkwrap.json*", "./"]

# Installer les dépendances
RUN npm install

# Copier tout le reste dans le répertoire de travail
COPY . .

# Définir les variables d'environnement pour l'application

ENV NODE_ENV=production
EXPOSE 3000

# Démarrer l'application
CMD ["npm", "start"]

