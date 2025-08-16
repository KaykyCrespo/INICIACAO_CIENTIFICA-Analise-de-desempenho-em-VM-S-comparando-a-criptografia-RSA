# 🔐 Cryptography Performance Benchmark in Virtualized Environments

[![Python](https://img.shields.io/badge/Python-3.7.3-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Research](https://img.shields.io/badge/Research-Scientific%20Initiation-orange.svg)](https://unip.br)

> **Análise Comparativa de Desempenho de Algoritmos Criptográficos em Ambientes Virtualizados**  
> *Pesquisa de Iniciação Científica - Universidade Paulista (UNIP)*

## 📊 Visão Geral

Esta pesquisa realizou uma análise sistemática e quantitativa do desempenho de algoritmos criptográficos assimétricos em ambientes virtualizados, revelando que **Ed25519 é 250x mais rápido que RSA 2048 bits** na geração de chaves.

### 🎯 Principais Descobertas

- **Ed25519/X25519**: Superiores em todas as métricas (tempo, CPU, memória)
- **RSA**: Degradação não-linear com aumento do tamanho da chave
- **Curvas NIST**: Performance intermediária, mas superiores ao RSA
- **Paralelização**: RSA se beneficia mais, mas não compensa diferença absoluta

## 🚀 Quick Start

### Pré-requisitos

```bash
Python 3.7.3+
Oracle VirtualBox 6.1+ (para replicar ambiente original)
```

### Instalação

```bash
git clone https://github.com/[seu-usuario]/cryptography-benchmark
cd cryptography-benchmark
pip install -r requirements.txt
```

### Execução Básica

```bash
# Executar benchmark completo
python src/benchmark_framework.py

# Executar apenas algoritmos específicos
python src/benchmark_framework.py --algorithms ed25519,rsa_2048

# Análise dos dados existentes
python src/analysis/generate_report.py
```

## 📁 Estrutura do Projeto

```
cryptography-benchmark/
├── 📄 README.md
├── 📄 requirements.txt
├── 📄 LICENSE
├── 📁 src/
│   ├── 🐍 benchmark_framework.py      # Framework principal
│   ├── 📁 algorithms/
│   │   ├── 🐍 rsa_impl.py            # Implementação RSA
│   │   ├── 🐍 ecc_impl.py            # Curvas Elípticas
│   │   └── 🐍 nist_curves.py         # Curvas NIST
│   ├── 📁 analysis/
│   │   ├── 🐍 data_processor.py      # Processamento de dados
│   │   ├── 🐍 visualizer.py          # Geração de gráficos
│   │   └── 🐍 generate_report.py     # Relatórios automáticos
│   └── 📁 utils/
│       ├── 🐍 system_monitor.py      # Monitoramento do sistema
│       └── 🐍 config.py              # Configurações
├── 📁 data/
│   ├── 📁 raw_results/               # Dados brutos coletados
│   ├── 📁 processed/                 # Dados processados
│   └── 📁 sample/                    # Dados de exemplo
├── 📁 docs/
│   ├── 📄 methodology.md             # Metodologia detalhada
│   ├── 📄 results_analysis.md        # Análise dos resultados
│   └── 📁 images/                    # Gráficos e imagens
└── 📁 tests/
    ├── 🐍 test_framework.py          # Testes unitários
    └── 🐍 test_algorithms.py         # Testes dos algoritmos
```

## 📈 Resultados Principais

### Performance de Geração de Chaves (ms)

| Algoritmo | 2 cores | 4 cores | 6 cores | Speedup |
|-----------|---------|---------|---------|---------|
| **Ed25519** | 0.099 | 0.277 | 0.095 | **1.3x** |
| **X25519** | 0.092 | 0.647 | 0.085 | **1.2x** |
| **RSA 2048** | 31.8 | 325.5 | 45.0 | **1.6x** |
| **RSA 4096** | 686.8 | 2661.1 | 800.0 | **1.8x** |

### Consumo de Recursos

| Algoritmo | RAM (MB) | CPU (%) | Eficiência |
|-----------|----------|---------|------------|
| **Ed25519** | 2.8 | 9 | ⭐⭐⭐⭐⭐ |
| **X25519** | 2.5 | 8 | ⭐⭐⭐⭐⭐ |
| **NIST P-256** | 5.2 | 12 | ⭐⭐⭐⭐ |
| **RSA 2048** | 21.4 | 38 | ⭐⭐ |
| **RSA 4096** | 38.2 | 45 | ⭐ |

## 🔬 Metodologia

### Ambiente de Teste
- **Virtualização**: Oracle VirtualBox 6.1
- **SO**: Windows 11 Professional (64 bits)
- **Configurações**: 2, 4, 6 núcleos × 0.5GB, 1.0GB RAM
- **Repetições**: 20 execuções por configuração
- **Biblioteca**: cryptography v36.0.1

### Métricas Coletadas
- ⏱️ **Tempo de execução** (precisão de microssegundos)
- 🧠 **Uso de memória** (picos durante operação)
- ⚡ **Utilização de CPU** (percentual por núcleo)
- ✅ **Taxa de sucesso** (operações completadas)

## 📊 Visualizações

### Gráfico de Performance
![Performance Comparison](docs/images/performance_comparison.png)

### Análise de Recursos
![Resource Usage](docs/images/resource_analysis.png)

## 🛠️ Uso Avançado

### Configuração Personalizada

```python
# config.py
BENCHMARK_CONFIG = {
    'algorithms': ['ed25519', 'x25519', 'rsa_2048', 'rsa_4096'],
    'cpu_cores': [2, 4, 6],
    'memory_configs': ['512MB', '1GB'],
    'repetitions': 20,
    'timeout': 60,
    'output_format': 'csv'
}
```

### Adicionando Novos Algoritmos

```python
# algorithms/custom_algorithm.py
from .base_algorithm import BaseAlgorithm

class CustomAlgorithm(BaseAlgorithm):
    def __init__(self):
        super().__init__("custom_algo")
    
    def generate_keys(self):
        # Implementação personalizada
        pass
    
    def sign(self, data, private_key):
        # Implementação de assinatura
        pass
```

## 📚 Documentação

- 📖 [Metodologia Completa](docs/methodology.md)
- 📊 [Análise de Resultados](docs/results_analysis.md)
- 🔧 [Guia de Configuração](docs/configuration.md)
- 🧪 [Reproduzindo Experimentos](docs/reproduction_guide.md)

## 🤝 Contribuições

Contribuições são bem-vindas! Por favor, veja nosso [Guia de Contribuição](CONTRIBUTING.md).

### Como Contribuir
1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`)
3. Commit suas mudanças (`git commit -am 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

## 📜 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 📖 Citação

Se você usar este trabalho em sua pesquisa, por favor cite:

```bibtex
@misc{andrade2025cryptobenchmark,
  title={Análise Comparativa de Desempenho de Algoritmos Criptográficos em Ambientes Virtualizados},
  author={Andrade, Caio Pacheco and Santos, Kayky Crespo},
  year={2025},
  institution={Universidade Paulista - UNIP},
  type={Iniciação Científica},
  url={https://github.com/[seu-usuario]/cryptography-benchmark}
}
```

## 👥 Autores

- **Caio Pacheco Andrade** - *Pesquisador Principal* - [GitHub](https://github.com/[caio-usuario])
- **Kayky Crespo Santos** - *Pesquisador Principal* - [GitHub](https://github.com/[kayky-usuario])

## 🎓 Instituição

**Universidade Paulista (UNIP)**  
Vice-Reitoria de Pós-Graduação e Pesquisa  
Programa de Iniciação Científica e Desenvolvimento Tecnológico e Inovação

## 📞 Contato

- 📧 Email: [caio.email@unip.br](mailto:caio.email@unip.br)
- 📧 Email: [kayky.email@unip.br](mailto:kayky.email@unip.br)
- 🌐 Site: [https://unip.br](https://unip.br)

## 🔗 Links Relacionados

- [Relatório Final (PDF)](docs/relatorio_final.pdf)
- [Apresentação](docs/apresentacao.pdf)
- [Dados Brutos](data/raw_results/)
- [Biblioteca Cryptography](https://cryptography.io/)

---

<div align="center">

**⭐ Se este projeto foi útil para você, considere dar uma estrela!**

[![Star History Chart](https://api.star-history.com/svg?repos=[seu-usuario]/cryptography-benchmark&type=Date)](https://star-history.com/#[seu-usuario]/cryptography-benchmark&Date)

</div>

---

> 💡 **Dica**: Este framework pode ser facilmente adaptado para avaliar novos algoritmos criptográficos, incluindo implementações pós-quânticas como CRYSTALS-Kyber e FALCON.

*Última atualização: Janeiro 2025*