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
image sera 28x28.



![34](https://user-images.githubusercontent.com/78183237/138888571-c27744d7-eff3-401f-838c-29e3952515b6.png)


le générateur essaie constamment de
déjouer le discriminateur en générant de mieux en mieux des faux, tandis que le discriminateur s’efforce de devenir un meilleur détective et de classer correctement les
images réelles et fausses. L’équilibre de ce jeu est lorsque le générateur génère des
contrefaçons parfaites qui semblent provenir directement des données d’apprentissage, et que le discriminateur doit toujours deviner à 0.5 de confiance que la sortie
du générateur est réelle ou fausse. Ce qui finit par se produire, c’est que le générateur apprend à rendre au discriminateur des données impossibles à distinguer des
données réelles.
