CREATE TABLE Nodes (
    NodeId INT PRIMARY KEY IDENTITY(1,1),
    IpAddress VARCHAR(50) NOT NULL,
    Port INT NOT NULL,
    PublicKey VARCHAR(255) NOT NULL,
    Status VARCHAR(50) NOT NULL -- "Online", "Offline"
);

CREATE TABLE NetworkConfig (
    ConfigId INT PRIMARY KEY IDENTITY(1,1),
    ConsensusMechanism VARCHAR(50) NOT NULL,
    NumberOfNodes INT NOT NULL
);

CREATE TABLE Transactions (
    TransactionId INT PRIMARY KEY IDENTITY(1,1),
    SenderId INT NOT NULL,
    ReceiverId INT NOT NULL,
    Amount DECIMAL(10,2) NOT NULL,
    Timestamp DATETIME NOT NULL,
    FOREIGN KEY (SenderId) REFERENCES Nodes(NodeId),
    FOREIGN KEY (ReceiverId) REFERENCES Nodes(NodeId)
);
