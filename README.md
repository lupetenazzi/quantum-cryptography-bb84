Aqui está:

---

# Quantum Cryptography - BB84

Simulação do protocolo BB84 para Distribuição de Chaves Quânticas (QKD) com análise do QBER sob diferentes níveis de interceptação, utilizando Qiskit.


## Sobre

Este repositório contém o código utilizado e desenvolvido para simulação e análise do QBER com Qiskit. Aqui, é analisado o protocolo BB84 por meio de simulação computacional, investigando a relação entre a taxa de interceptação e o *Quantum Bit Error Rate* (QBER). A abordagem adota ferramentas acessíveis e de código aberto, priorizando a reprodutibilidade em hardware convencional.

**Autor:**
- [Luiza Faria Petenazzi](mailto:luiza.petenazzi@sou.inteli.edu.br) — Instituto de Tecnologia e Liderança (Inteli)



## Estrutura do repositório

```
quantum-cryptography-bb84/
├── notebooks/
│   ├── bb84.ipynb           # Protocolo BB84 sem interceptação
│   └── bb84_noise.ipynb     # Protocolo BB84 com interceptação (ataque intercept-resend)
├── requirements.txt
├── LICENSE
└── README.md
```



## Protocolo BB84

O BB84 é um dos primeiros protocolos de Distribuição de Chaves Quânticas, proposto por Bennett e Brassard em 1984. Ele permite que duas partes — Alice (emissora) e Bob (receptor) — estabeleçam uma chave criptográfica segura por meio de um canal quântico, explorando propriedades da mecânica quântica para detectar a presença de um interceptador (Eve).

A métrica central deste estudo é o **QBER** (*Quantum Bit Error Rate*):

$$QBER = \frac{N_{erros}}{N_{total}}$$

Em um cenário de interceptação total via ataque *intercept-resend*, o valor esperado do QBER converge para aproximadamente **25%**.


## Experimentos

| Cenário | Descrição | QBER esperado |
|---|---|---|
| Sem interceptação | Protocolo executado sem Eve | ≈ 0% |
| Com interceptação (25%) | Ataque *intercept-resend* em 25% dos qubits | ≈ 6,25% |
| Com interceptação (50%) | Ataque *intercept-resend* em 50% dos qubits | ≈ 12,5% |
| Com interceptação (75%) | Ataque *intercept-resend* em 75% dos qubits | ≈ 18,75% |
| Com interceptação (100%) | Ataque *intercept-resend* em todos os qubits | ≈ 25% |

**Parâmetros:** 200 qubits por execução, 50 execuções independentes por cenário, totalizando 250 simulações.


## Como reproduzir

### Pré-requisitos

```bash
pip install -r requirements.txt
```

### Executando os notebooks

```bash
# Cenário sem interceptação
jupyter notebook notebooks/bb84.ipynb

# Cenário com interceptação
jupyter notebook notebooks/bb84_noise.ipynb
```

Os parâmetros `n_qubits`, `n_runs` e `eve_fraction` podem ser ajustados diretamente no código para replicar os cenários analisados ou explorar novas configurações.


## Atribuições

A implementação foi inspirada e adaptada a partir do trabalho de **Kejvi (2023)**:

> Kejvi, K. (2023). *Building a Quantum Key Distribution System with Qiskit: A Hands-On Guide to BB84*. Medium.
> Disponível em: https://medium.com/@kejvikejvi/building-a-quantum-key-distribution-system-with-qiskit-a-hands-on-guide-to-bb84-7cc49ab72baa


## Dependências

| Pacote | Versão |
|---|---|
| qiskit | latest |
| qiskit-aer | latest |
| numpy | 1.26.4 |
| matplotlib | 3.8.2 |

