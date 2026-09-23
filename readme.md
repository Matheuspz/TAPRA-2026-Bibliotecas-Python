# TAPRA-2026-Bibliotecas-Python

### Qual é o objetivo principal da biblioteca?
- Pyodbc
>Permitir que aplicativos escritos em Python se conectem e interajam com bancos de dados relacionais usando o padrão ODBC
- SQLAlchemy
>Fornecer uma forma eficiente, flexível e de alto desempenho para interagir com bancos de dados relacionais usando a linguagem Python



### Que tipo de banco de dados ela permite acessar?

### Ela é mais indicada para bancos relacionais ou não relacionais?
- Pyodbc

>Bancos relacionais

- SQLAlchemy

>Bancos relacionais


### A biblioteca trabalha com SQL puro, ORM ou ambos?

### Como é feita a instalação?
- Pyodbc

```
pip install pyodbc
```

```
from typing import List
from typing import Optional
from sqlalchemy import ForeignKey
from sqlalchemy import String
from sqlalchemy.orm import DeclarativeBase
from sqlalchemy.orm import Mapped
from sqlalchemy.orm import mapped_column
from sqlalchemy.orm import relationship

class Base(DeclarativeBase):
    pass

class User(Base):
    __tablename__ = "user_account"
    id: Mapped[int] = mapped_column(primary_key=True)
    name: Mapped[str] = mapped_column(String(30))
    fullname: Mapped[Optional[str]]
    addresses: Mapped[List["Address"]] = relationship(
        back_populates="user", cascade="all, delete-orphan"
    )
    def __repr__(self) -> str:
        return f"User(id={self.id!r}, name={self.name!r}, fullname={self.fullname!r})"

class Address(Base):
    __tablename__ = "address"
    id: Mapped[int] = mapped_column(primary_key=True)
    email_address: Mapped[str]
    user_id: Mapped[int] = mapped_column(ForeignKey("user_account.id"))
    user: Mapped["User"] = relationship(back_populates="addresses")
    def __repr__(self) -> str:
        return f"Address(id={self.id!r}, email_address={self.email_address!r})"
```
### Como é criado um exemplo simples de conexão?
- Pyodbc
```
import pyodbc
cnxn = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER=localhost;DATABASE=testdb;UID=me;PWD=pass')
cursor = cnxn.cursor()
```
### Como executar uma consulta *SELECT* simples?
- Pyodbc
```
cursor.execute("select user_id, user_name from users")
row = cursor.fetchone()
if row:
  print(row)
```
### Bibliotecas: SQLAlchemy e Pyodbc
