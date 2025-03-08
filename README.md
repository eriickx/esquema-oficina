# esquema-oficina
Esquema conceitual para uma oficina feito com o DBDesigner.

# Markup
Segue o markup do esquema

```bash
ORDEM_SERVICO {
	ID integer pk increments unique
	DESCRICAO varchar(45)
	STATUS integer *> STATUS.ID
	VALOR_TOTAL decimal
	DATA_EMISSAO timestamp
	DATA_CONCLUSAO timestamp
	ID_FICHA integer > FICHA.ID
}

CLIENTE {
	ID integer pk increments unique
	NOME varchar(45)
	TELEFONE varchar(11)
	ENDERECO varchar(45)
}

MECANICO {
	ID integer pk increments unique
	NOME varchar(45)
	ENDERECO varchar(45)
	ESPECIALIDADE integer *> ESPECIALIDADE.ID
}

ESPECIALIDADE {
	ID integer pk increments unique
	DESCRICAO varchar(45)
}

VEICULO {
	ID integer pk increments unique
	PLACA varchar(7) unique
	MARCA varchar(45)
	MODELO varchar(45)
	ANO integer
	COR varchar(45)
}

SERVICO {
	ID integer pk increments unique
	NOME varchar(45)
	DESCRICAO varchar(45)
	DATA_EMISSAO timestamp
	DATA_CONCLUSAO timestamp
	STATUS integer *> STATUS.ID
	VALOR_TOTAL decimal
}

PEÇA {
	ID integer pk increments unique
	NOME varchar(45)
	VALOR_UNITARIO decimal
}

FICHA {
	ID integer pk increments unique
	STATUS integer *> STATUS.ID
	ID_CLIENTE_ENTRADA integer *> CLIENTE.ID
	ID_CLIENTE_RETIRADA integer *> CLIENTE.ID
	ID_VEICULO integer *> VEICULO.ID
	DATA_ENTRADA timestamp
	DATA_SAIDA timestamp
}

STATUS {
	ID integer pk increments unique
	NOME varchar(45)
}

SERVICO_MECANICO {
	ID_SERVICO integer pk *> SERVICO.ID
	ID_MECANICO integer pk *> MECANICO.ID
	VALOR decimal
}

ORDEM_SERVICO_SERVICO {
	ID_ORDEM_SERVICO integer pk *> ORDEM_SERVICO.ID
	ID_SERVICO integer pk *> SERVICO.ID
}

SERVICO_PECA {
	ID_SERVICO integer pk *> SERVICO.ID
	ID_PECA integer pk *> PEÇA.ID
	QUANTIDADE integer
	VALOR_TOTAL integer
}
```
