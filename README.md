# GAN
Dans ce test, nous allons implémenter un « Vanilla GAN » qui apprend à
produire des chiffres manuscrits. Nous utiliserons la bibliothèque de réseau neuronal Python Pytorch. La figure ci-dessous montre une architecture du GAN que nous avons
implémenter
Le discriminateur est entraîné comme un classificateur binaire où les étiquettes
positives correspondent à des images réelles et les étiquettes négatives correspondent
aux images générées. Le Générateur est entraîné comme un adversaire du discriminateur, Il prend z en entrée et produit une image 28 × 28 × 1 et Il est entraîné pour
maximiser la perte du discriminateur et est mis à jour en rétropropageant la perte
à travers le réseau du discriminateur vers le réseau du générateur. nous allons définir les réseaux de neurones, en commençant par le discriminateur. Ce réseau prendra une
image aplatie en entrée et renvoi la probabilité qu’elle appartienne au jeu
de données réel ou au jeu de données synthétique. La taille d’entrée pour chaque
image sera 28x28. Concernant la structure de ce réseau, il aura trois couches cachées, chacune suivie d’une non-linéarité Leaky-ReLU, , nous utilisons la fonction
d’activation Leaky ReLU. Contrairement à une fonction ReLU régulière, qui mappe
toute entrée négative à 0, Leaky ReLU permet un petit gradient positif. Cela empêche les gradients de disparaître pendant l’entraî- nement, ce qui tend à donner
de meilleurs résultats d’entraînement. et d’une couche Dropout pour éviter le surapprentissage. Une fonction Sigmoïde est appliquée à la sortie à valeur réelle pour
obtenir une valeur dans la plage (0, 1). D’autre part, le réseau génératif prend un
vecteur de variable latente en entrée et renvoie un vecteur de valeur 784, ce qui correspond à une image 28x28 aplatie. Et le but de ce réseau est d’apprendre à créer
des images indiscernables de chiffres manuscrits, c’est pourquoi sa sortie est ellemême une nouvelle image. Ce réseau aura trois couches cachées, chacune suivie
d’une non-linéarité Leaky-ReLU. La couche de sortie aura une fonction d’activation
TanH, , qui mappe les valeurs résultantes dans la plage (-1, 1). La raison de l’utilisation de tanh (par opposition à, disons, sigmoïde, qui produirait des valeurs dans
la plage plus typique de 0 à 1) est que tanh a tendance à produire des images plus
nettes. nous utiliserons Adam comme algorithme d’optimisation pour les deux ré-
seaux de neurones, avec un taux d’apprentissage de 0,0002. Le taux d’apprentissage
proposé a été obtenu après des tests avec plusieurs valeurs, bien que ce ne soit pas
nécessairement la valeur optimale pour cette tâche. La fonction de perte que nous
utiliserons pour cette tâche s’appelle Binary Cross Entopy Loss (BCE Loss), L’entropie croisée binaire est une mesure de la différence entre les probabilités calculées et
les probabilités réelles pour les prédictions avec seulement deux classes possibles, et elle sera utilisée pour ce scénario car elle ressemble à la perte pour le générateur 
et le
discriminateur. Plus précisément, nous prendrons la moyenne des pertes calculées
pour chaque mini-lot. Pendant l’entrainement, le générateur essaie constamment de
déjouer le discriminateur en générant de mieux en mieux des faux, tandis que le discriminateur s’efforce de devenir un meilleur détective et de classer correctement les
images réelles et fausses. L’équilibre de ce jeu est lorsque le générateur génère des
contrefaçons parfaites qui semblent provenir directement des données d’apprentissage, et que le discriminateur doit toujours deviner à 0.5 de confiance que la sortie
du générateur est réelle ou fausse. Ce qui finit par se produire, c’est que le générateur apprend à rendre au discriminateur des données impossibles à distinguer des
données réelles.

