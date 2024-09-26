Arduino-based system designed to control acoustic plucked instruments with stepper motor utilizing MIDI messages 

l'idée est de faire un systeme qui viend jouer d'un instrument a corde gratée (ukulele, guitare, basse, etc ...) depuis des messages midi.

# Les choix techniques 

on utilisera un systeme de driver et moteur pas à pas pour deplacer la position du "doigt d'accord" de la corde. il faut aussi penser au caprteur de fin de course pour initialiser la position du moteur.
<img src="https://github.com/glloq/Continuous_PluckStepper/blob/main/img/guide%20lineaire.png" alt="Your image title" width=100% height=100%/>  
nous avons deux facons de faire le systeme :
-un systeme toujours en contact avec la corde (bottleneck ou slide)

-ou un systeme de doigt mecanique qui est descendu pour actionner une frette avec un servomoteur ou un solenoide.
Directement sur le chariot:

ou en deporté pour eviter les cables elecrtique en mouvement:
<img src="https://github.com/glloq/OneStringGuitar/blob/main/img/bowden.png" alt="bowden" width=80% height=80%/>  

On utilisera le meme type d'actionneur pour le grattage de la corde 
<img src="https://github.com/glloq/Continuous_PluckStepper/blob/main/img/grattage.png" alt="bowden" width=100% height=100%/>  

## Le code 

Je ne ferait que une version du code avec l'utilisation de servomoteurs pour les actions sur la/les cordes; il y aura deux cas d'utilisation avec ou sans actionneur sur le doigt  (pour l'instant) 
Le code est concu pour etre adaptable a plusieurs instrument, il suffira d'adapter le fichier settings.h en fonction de l' utilisation.

Nous utiliserons une carte pca9685 pour controller le ou les servomoteurs de chaque corde.
<img src="https://github.com/glloq/Continuous_PluckStepper/blob/main/img/SchemasActionneurs.png" alt="SchemasActionneurs." width=70% height=70%/>  

de la meme maniere que pour la technique avec les solenoides ou les servomoteurs, nous declarerons les parametre de chaque corde dans un tableau de struct:
```
struct StringMapping {
    int firstNote;//midi note open string
    int fretNbr; // numbers of frets per string
    int pinStep;//
    int pinDir;//
    int pinEndStop;    //pin of the end course
    int homePosition; //space between the end course and the open string in mm
    bool inverseDirection;    // inverse the direction of the motor if true 
    int servoFingerPin;   // pin servo finger on the pca9685
    int servoPluckPin;   //  pin servo pluck on the pca9685
    int angleServoPluck;// angle of the servo pluck when touching the cord
    int angleServoFingerOpen;// angle of the servoFinger above the cord
    int angleServoFingerClose;// angle of the servoFinger touching the cord
};
```
### struture du code






