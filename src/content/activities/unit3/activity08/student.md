Hay una gran diferencia entre las dos líneas, pues una de ellas está tomando el VALOR de velocity al usar su copia, y la otra está usando paso por referencia. El problema
de usar el paso por referencia es que esa línea modificará el valor de velocity en el resto del código. La copia usará también los datos de velocity pero no afectará
el objeto globalmente al usar la copia.
