# Sistema-de-Controle
Sistema de Controle de Aluguel de Veículos

import sqlite3

conn = sqlite3.connect('aluguel_veiculos.db')
cursor = conn.cursor()

cursor.execute('''CREATE TABLE clientes (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    telefone TEXT
)''')

cursor.execute('''CREATE TABLE veiculos (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    modelo TEXT NOT NULL,
    placa TEXT NOT NULL,
    status TEXT NOT NULL
)''')

cursor.execute('''CREATE TABLE contratos (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    cliente_id INTEGER,
    veiculo_id INTEGER,
    data_inicio TEXT,
    data_fim TEXT,
    FOREIGN KEY (cliente_id) REFERENCES clientes(id),
    FOREIGN KEY (veiculo_id) REFERENCES veiculos(id)
)''')

conn.commit()
conn.close()
