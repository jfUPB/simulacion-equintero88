### ¿Por qué es necesario multiplicar la aceleración por cero en cada frame?

Esto es necesario porque las fuerzas se están apicando en cada momento dado, y si no se multiplica por cero, las fuerzas se estarían acumulando unas sobre otras, 
modificando el efecto de las fuerzas tal como las planteamos y probablemente llegando a un punto de descontrol total.

### ¿Por qué se multiplica por cero justo al final de update()?

Porque ya el efecto de la aceleración (afectada por las fuerzas) se ha aplicado sobre la velocidad en la primera línea, y esta ha hecho lo propio con la posición, 
entonces puede hacerse cero porque no afectará y en el otro frame tendrá de nuevo sus fuerzas listas para aplicar.
