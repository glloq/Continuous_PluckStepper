Arduino-based system designed to control acoustic plucked instruments with stepper motor utilizing MIDI messages 

l'idée est de faire un systeme qui viend jouer d'un instrument a corde gratée (ukulele, guitare, basse, etc ...) depuis des messages midi.

# Les choix techniques 
Avec un driver et un moteur pas a pas, on peut faire un reglage des positions via software.
On pourra utiliser des solenoides ou des servomoteurs pour les actions de grattage et/ou doigt.

### accords
on deplace un systeme de doigt pour actionner l'accord de la corde 
<img src="https://github.com/glloq/OneStringGuitar/blob/main/img/guide%20lineaire.png" alt="Your image title" width=80% height=80%/>

<img src="https://github.com/glloq/OneStringGuitar/blob/main/img/bowden.png" alt="bowden" width=80% height=80%/>

### grattage 
