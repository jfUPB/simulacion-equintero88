La solucuón a este problema lo revisé desde la actividad 3, y lo que sucede con ese fragmento de código es que la aceleración está tomando el valor de la fueza que 
se está llamando en applyForce(), por lo que por ejemplo, en este código, la aceleración está siendo igual solamenta a la gravedad. El viento no está afectando de 
ninguna manera este valor. La solución que proponen en el libro es la siguiente:

```js
applyForce(force)
{
this.acceleration.add(force);
}
```
De esta forma se están sumando todas las fuerzas que están actuando al valor de la aceleración.
