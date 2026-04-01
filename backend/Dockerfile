# Stage 1 : on installe tout et on lance les tests pour vérifier que le code marche.
# Stage 2 : on repart de zéro avec juste ce qu'il faut pour faire tourner l'app en prod.
# Résultat : Cela permet de réduire la taille de l’image finale, de limiter la surface d’attaque et d’éviter d’embarquer les outils de développement en production.


FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm test

FROM node:20-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install --omit=dev
COPY server.js .
EXPOSE 3000
CMD ["node", "server.js"]
