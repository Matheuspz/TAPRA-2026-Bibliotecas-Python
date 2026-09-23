# TAPRA-2026-Bibliotecas-Python

### Qual é o objetivo principal da biblioteca?

### Que tipo de banco de dados ela permite acessar?

### Ela é mais indicada para bancos relacionais ou não relacionais?

### A biblioteca trabalha com SQL puro, ORM ou ambos?

### Como é feita a instalação?
- Pyodbc

```
pip install pyodbc
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
