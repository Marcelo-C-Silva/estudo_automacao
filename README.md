# Automação de Coleta de Logos e Marcas com Python

[![Python](https://img.shields.io/badge/Python-3.8+-blue)](https://www.python.org/)

---

## **Descrição do Projeto**

Este projeto automatiza a coleta de **logos, brasões e marcas** de uma lista de sites e gera um **documento Word organizado** contendo:

* Nome e link das imagens (links reais substituídos por exemplos para preservar privacidade);
* Tamanho real das imagens (em pixels);
* Dimensões declaradas no HTML (quando disponíveis);
* Inserção das imagens (quando compatível com Word).

O objetivo é **transformar uma tarefa manual de dias em um processo automatizado de horas**, auxiliando o time de design a identificar rapidamente quais imagens precisam ser atualizadas.

---

## **Stack e Bibliotecas Utilizadas**

* **Python 3.8+**: linguagem principal;
* **Selenium**: automação de navegação em sites dinâmicos;
* **BeautifulSoup4**: parsing de HTML e extração de imagens;
* **Requests**: download das imagens;
* **Pillow (PIL)**: análise de imagens e captura de dimensões;
* **Python-docx**: criação automática de documento Word;
* **webdriver-manager**: gerenciamento automático do driver do Chrome.

---

## **Pré-requisitos**

1. **Python 3** instalado
2. **Google Chrome** instalado
3. Instalar as bibliotecas necessárias:

```bash
pip install selenium beautifulsoup4 requests pillow python-docx webdriver-manager
```

---

## **Como Executar**

1. Clone ou baixe o repositório:

```bash
git clone https://github.com/seu-usuario/automacao-logos.git
cd automacao-logos
```

2. Abra o script `coletar_logos.py` e configure a lista de sites:

```python
sites = [
    "https://exemplo-site1.com/",
    "https://exemplo-site2.com/",
    "https://exemplo-site3.com/"
]
```

> ⚠ **Observação:** os links reais da empresa foram substituídos por exemplos genéricos para **preservar privacidade e segurança**.

3. Execute o script:

```bash
python coletar_logos.py
```

4. Ao final, será gerado um documento Word:

```
logos_brasoes_marcas_sites_demo.docx
```

contendo todas as informações coletadas.

---

## **Como Funciona o Script**

1. **Inicialização do navegador:**
   O Selenium abre cada site usando o Chrome em modo **headless** (sem interface gráfica).

2. **Extração de imagens:**
   O BeautifulSoup analisa o HTML e encontra todas as tags `<img>` com palavras-chave: `"logo"`, `"brasao"` ou `"marca"`.

3. **Download e análise das imagens:**
   O Requests baixa cada imagem e o Pillow obtém as dimensões reais.
   SVGs são ignorados, pois o Word não os suporta.

4. **Geração do documento Word:**
   O python-docx insere:

* URL da imagem
* Tamanho real
* Dimensões HTML
* A própria imagem (quando suportada)

5. **Tratamento de erros:**

* Imagens inacessíveis (HTTP 403/404) são registradas;
* Formatos incompatíveis com Word recebem aviso no documento.

---

## **Configurações e Customizações**

* **Lista de sites:** altere a variável `sites` para qualquer URL que deseja analisar.
* **Palavras-chave de filtro:** atualmente `"logo"`, `"brasao"` e `"marca"`. Podem ser alteradas na linha:

```python
if any(keyword in src.lower() or keyword in alt.lower() for keyword in ["logo", "brasao", "marca"]):
```

* **Tempo de espera:** o `time.sleep(3)` garante que conteúdo dinâmico carregue. Ajuste conforme necessário.

---

## **Resultado Esperado**

Documento Word com:

```
🔗 Site: https://exemplo-site1.com/
🟢 Imagens encontradas no site:
- https://exemplo-site1.com/imagem/logo1.png
Imagem: https://exemplo-site1.com/imagem/logo1.png
➡ Tamanho real: 400x200px | HTML: 200x100
```

---

## **Observações Importantes**

* **Privacidade:** links reais foram removidos para evitar exposição de sistemas internos.
* **Compatibilidade Word:** imagens SVG não são inseridas, mas listadas.
* **Extensibilidade:** o script pode ser adaptado para gerar relatórios em Excel, PDF ou HTML.

---

## **Resultado e Aprendizado**

Esta foi uma das minhas **primeiras experiências com Python e automação**, transformando uma tarefa manual de dias em algo que pode ser feito em horas. A escolha das bibliotecas certas e a lógica de extração e geração de relatórios mostram como **automação pode agregar eficiência real em processos de trabalho**.


