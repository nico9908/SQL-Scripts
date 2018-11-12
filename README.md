CREATE TABLE INVOICE (
	InvoiceNumber			Int				NOT NULL,
	InvoiceDate			DateTime2			NOT NULL,
	SubTotal			Float				NOT NULL,
	TaxPct				Float				NOT NULL,
	Total				Float				NOT NULL,
	CONSTRAINT			INVOICE_PK			PRIMARY KEY(InvoiceNumber)
	);

CREATE TABLE PRODUCT (
	ProductNumber			Int				NOT NULL,
	ProductType			NVarChar(25)			NOT NULL,
	ProductDescription		NVarChar(50)			NOT NULL,
	UnitPrice			Float				NOT NULL,
	CONSTRAINT			PRODUCT_PK			PRIMARY KEY(ProductNumber)
	);

CREATE TABLE LINE_ITEM (
	InvoiceNumber			Int				NOT NULL,
	LineNumber			Int				NOT NULL,
	ProductNumber			Int				NOT NULL,
	Quantity			Int				NOT NULL,
	UnitPrice			Float				NOT NULL,
	Total				Float				NOT NULL,
	CONSTRAINT			LINE_ITEM_PK			PRIMARY KEY(InvoiceNumber, LineNumber),
	CONSTRAINT			InvoiceNumber_FK		FOREIGN KEY	(InvoiceNumber)
								REFERENCES INVOICE (InvoiceNumber)
								ON UPDATE CASCADE,
	CONSTRAINT			ProductNumber_FK		FOREIGN KEY (ProductNumber)
								REFERENCES PRODUCT (ProductNumber)
								ON UPDATE CASCADE
