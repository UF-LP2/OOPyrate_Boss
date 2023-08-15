# OOPIrate_Boss

En este repositorio podrá encontrar el esquema de Unit Test basado en pytest, apra realizar las pruebas unitarias del mini TP TP_OOPirate.
<br>La prueba del TP se realiza de forma automatizada utilizando Github Actions y se activará cuando se realice PUSH en la rama ENTREGA.
<br>Cuantos más TESTs pass tenga el TP, mejor valoración.

Se realizará la prueba de las tres clases (Ship, Cruise & Cargo), como también se realizará un test global del sistema.

## Test Cases
### test_ship.py
```python
import pytest
from src.ships import Ship

def test_is_ship() -> None:
    listaShip: list[int, int] = [
        [23, 123],
        [123, 34],
        [78, 15],
        [23, 30]
    ]
    
    with pytest.raises(ValueError):
        for ship in listaShip:
            ship: Ship = Ship(ship[0], ship[1])
            assert (ship.is_worth_it() >= 20) == True 
```
## test_cargo.py
```python
import pytest
from src.ships import Cargo


def test_is_cargo() -> None:
    listaCargos: list[int, float, int, int] = [
        [23, 0.25, 123, 45, ],
        [123, 1, 34, 34],
        [78, 0.5, 15, 65],
        [2, 0.25, 34, 70]
    ]
    
    with pytest.raises(ValueError): 
        for cargo in listaCargos:
            cargo: Cargo = Cargo(cargo[0], cargo[1], cargo[2], cargo[3])
            assert (cargo.is_worth_it() >= 20) == True
```
## test_cruise.py
```python
import pytest
from src.ships import Cruise
        
def test_is_Cruise() -> None:
    listaCruise: list[int, int, int] = [
        [23, 123, 45],
        [123, 34, 34],
        [78, 15, 65],
        [23, 30, 80]
    ]
    
    with pytest.raises(ValueError):
        for cruise in listaCruise:
            cruise: Cruise = Cruise(cruise[0], cruise[1], cruise[2])
            assert (cruise.is_worth_it() >= 20) == True 
```
