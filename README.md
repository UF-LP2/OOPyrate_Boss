# OOPyrate_Boss

En este repositorio podrá encontrar el esquema de Unit Test basado en pytest, apra realizar las pruebas unitarias del mini TP TP_OOPirate.
<br>La prueba del TP se realiza de forma automatizada utilizando Github Actions y se activará cuando se realice PUSH en la rama ENTREGA.
<br>Cuantos más <b>TESTS PASS</b> tenga el TP, mejor valoración.

Se realizará la prueba de las tres clases (Ship, Cruise & Cargo), como también se realizará un test general.
<br>El test general, descarga un archivo con muchos datos y llevará el código a sus limites.

## Test Cases
### test_ships.py
```python
def test_is_ship() -> None:
    listaShip: list[int, int] = [ """static data set""" ]
    
    with pytest.raises(ValueError):
        for ship in listaShip:
            ship: Ship = Ship(ship[0], ship[1])
            assert (ship.is_worth_it() >= 20) == True 
```
## test_cargos.py
```python
def test_is_cargo() -> None:
    listaCargos: list[int, float, int, int] = [ """static data set""" ]
    
    with pytest.raises(ValueError): 
        for cargo in listaCargos:
            cargo: Cargo = Cargo(cargo[0], cargo[1], cargo[2], cargo[3])
            assert (cargo.is_worth_it() >= 20) == True
```
## test_cruises.py
```python
def test_is_Cruise() -> None:
    listaCruise: list[int, int, int] = [ """static data set""" ]
    
    with pytest.raises(ValueError):
        for cruise in listaCruise:
            cruise: Cruise = Cruise(cruise[0], cruise[1], cruise[2])
            assert (cruise.is_worth_it() >= 20) == True 
```
## test_luffy.py
```python
def test_with_file():
    url="https://my.api.mockaroo.com/oop_pirate.csv?key=<key>"
    
    try:
        ShipLists = csv.reader(codecs.iterdecode(requests.get(url).iter_lines(), encoding="utf-8"), delimiter=",")
    except (requests.exceptions.ConnectionError, requests.exceptions.RequestException):
        ...
    else:
        myShips: list[any] = []
        header: bool = True
        for ship in ShipLists:
            if not header:
                try:
                    if ship[2] == '' and ship[3] == '':
                        myShips.append(Ship(int(ship[0]), int(ship[1])))
                    elif ship[3] == '':
                        myShips.append(Cruise(int(ship[2]), int(ship[0]), int(ship[1])))
                    else:
                        if ship[2] == '':
                            continue
                        myShips.append(Cargo(int(ship[2]), float(ship[3]), int(ship[0]), int(ship[1])))
                except ValueError:
                    continue
            else:
                header = False
        with pytest.raises(ValueError):
            for ship_ in myShips:
                assert (ship_.is_worth_it() >= 20) == True
```
---
##### UF-FICEN LP2 2023 - [Ezequiel Augusto Stanganelli](https://github.com/eastanganelli)
