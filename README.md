# FastAPI

[![FastAPI](https://img.shields.io/pypi/v/fastapi.svg)](https://pypi.org/project/fastapi/)
[![Python Version](https://img.shields.io/pypi/pyversions/fastapi.svg)](https://python.org)
[![Downloads](https://pepy.tech/badge/fastapi)](https://pepy.tech/project/fastapi)

FastAPI es un framework web moderno y rápido para construir APIs con Python 3.8+ basado en las anotaciones de tipos estándar de Python.

## Características

- **Rapidez:** Alto rendimiento, a la par con NodeJS y Go.
- **Rápido de programar:** Incrementa la velocidad de desarrollo entre 200% y 300%.
- **Menos errores:** Reduce los errores humanos aproximadamente un 40%.
- **Intuitivo:** Gran soporte en los editores con autocompletado. Gasta menos tiempo debugging.
- **Fácil:** Diseñado para ser fácil de usar y aprender. Gastando menos tiempo leyendo documentación.
- **Basado en estándares:** Compatible con OpenAPI (Swagger) y JSON Schema.

## Requisitos

- Python 3.8+

## Instalación

```bash
pip install fastapi
pip install "uvicorn[standard]"


## Este es el ejemplo que vamos a utilizar para ejecutarlo

from fastapi import FastAPI
from pydantic import BaseModel
from typing import Union

app = FastAPI()


class Item(BaseModel):
    name: str
    price: float
    is_offer: Union[bool, None] = None


@app.get("/")
def read_root():
    return {"Hello": "World"}


@app.get("/items/{item_id}")
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}


@app.put("/items/{item_id}")
def update_item(item_id: int, item: Item):
    return {"item_name": item.name, "item_id": item_id}


Estas son las paginas que necesitaremos para iniciarlizarlo

http://127.0.0.1:8000/docs#/default/update_item_items__item_id__put
http://127.0.0.1:8000/redoc#operation/read_root__get
