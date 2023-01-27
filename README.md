# PDSfabrica02.js

from abc import ABC, abstractmethod

class Veiculo(ABC):
    def __init__(self, modelo:str, marca:str, cor:str, numeroRodas:int):
        self.modelo = modelo
        self.marca = marca
        self.cor = cor
        self.numeroRodas = numeroRodas

    @abstractmethod
    def clone(self):
        pass

    def represent(self):
        return f"Modelo: {self.modelo}, Marca: {self.marca}, Cor: {self.cor}, Numero de Rodas: {self.numeroRodas}"

class Carro(Veiculo):
    def __init__(self, modelo:str, marca:str, cor:str, numeroRodas:int, numeroPortas:int, numeroAssentos:int):
        super().__init__(modelo, marca, cor, numeroRodas)
        self.numeroPortas = numeroPortas
        self.numeroAssentos = numeroAssentos

    def clone(self):
        return Carro(self.modelo, self.marca, self.cor, self.numeroRodas, self.numeroPortas, self.numeroAssentos)
    
    def represent(self):
        return f"{super().represent()}, Numero de Portas: {self.numeroPortas}, Numero de Assentos: {self.numeroAssentos}"

class Moto(Veiculo):
    def __init__(self, modelo:str, marca:str, cor:str, numeroRodas:int, tipo:str):
        super().__init__(modelo, marca, cor, numeroRodas)
        self.tipo = tipo

    def clone(self):
        return Moto(self.modelo, self.marca, self.cor, self.numeroRodas, self.tipo)
    
    def represent(self):
        return f"{super().represent()}, Tipo: {self.tipo}"

class Aplicacao:
    def __init__(self):
        self.veiculos = [Carro("Fusca","Volkswagen","Preto",4,4,4),
                         Carro("Gol","Volkswagen","Branco",4,4,4),
                         Moto("Harley","Harley Davidson","Preto",2,"Cruiser"),
                         Moto("Yamaha","Yamaha","Vermelho",2,"Esportiva"),
                         Carro("Uno","Fiat","Azul",4,4,4),
                         Moto("Honda","Honda","Verde",2,"Naked")]

    def get_clones(self):
        clones = []
        for veiculo in self.veiculos:
            clones.append(veiculo.clone())
        return clones


aplicacao = Aplicacao()
veiculos_clones = aplicacao.get
