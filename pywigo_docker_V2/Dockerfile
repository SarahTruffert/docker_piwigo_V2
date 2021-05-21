# Crée un calque à partir de l'image :
FROM alpine:3.10.3

# Copie fichier actuel dans le container :
COPY piwigo-11.4.0 /piwigo

# Installe les outils requis pour le projet + met à jour dépendances :
# --no cache : ne pas utiliser les données dans le cache
RUN apk --no-cache add curl php7 php7-gd php7-mysqli php7-json php7-session php7-exif

# Ajoute l'utilisateur :
RUN adduser -h /piwigo -DS piwigo 

# -o commande échoue si erreur
# RUN install -d -o piwigo /piwigo/piwigo/galleries /piwigo/piwigo/upload

# chown : a qui appartient / propriété
RUN chown -R piwigo /piwigo/piwigo/local

# chmod : permission accordé au dossier 
RUN chmod 777 -R /piwigo

# Modifie répertoire courant de travail par Piwigo :
WORKDIR /piwigo

# Si pas de privilèges spéciaux : 
USER piwigo

# Execute php sur le port 8000 sous le nom de piwigo :
CMD ["php","-S","0.0.0.0:8000","-t","piwigo"]
