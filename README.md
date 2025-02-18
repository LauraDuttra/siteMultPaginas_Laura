# Projeto Minimalix - Website Institucional 🌐

Este projeto consiste em um site fictício desenvolvido para fins didáticos, demonstrando um modelo de página institucional para uma empresa chamada **Minimalix**. A página abrange as seções de **Home**, **Serviços** e **Contato**.

## Estrutura do Projeto 🗂️

Este repositório contém o código de três páginas principais:

1. **Home (index.html)** 🏠: Página inicial com uma introdução ao site e seus principais serviços.
2. **Serviços (servicos.html)** 🛠️: Página que detalha os serviços oferecidos pela empresa.
3. **Contato (contato.html)** 📧: Página com um formulário de contato, onde os usuários podem preencher suas informações.

### Funcionalidades e Descrição 📑

#### 1. **Página Inicial (index.html)** 🏠

A página inicial apresenta um cabeçalho com o logo e um menu de navegação. A seção principal destaca os serviços da empresa, como o desenvolvimento web, design gráfico e marketing digital. A página também inclui uma introdução sobre os serviços oferecidos e informações de localização da empresa.

#### 2. **Página de Serviços (servicos.html)** 🛠️

Esta página descreve os principais serviços oferecidos pela **Minimalix**, como:

- **Desenvolvimento Web** 💻
- **Design Gráfico** 🎨
- **Marketing Digital** 📈
- **Consultoria e Treinamento** 📚

Além disso, a página inclui uma galeria de imagens, permitindo a visualização em tela cheia usando o recurso Lightbox.

#### 3. **Página de Contato (contato.html)** 📧

Na página de contato, os usuários podem preencher um formulário com suas informações pessoais, como nome, e-mail, telefone, e até mesmo o CEP. O formulário está configurado para enviar os dados para o serviço **Formspree**, facilitando a coleta de informações sem a necessidade de configurar um backend.

## Estrutura dos Arquivos 🗃️

- **index.html** 🏠: Contém a estrutura da página inicial.
- **servicos.html** 🛠️: Contém a estrutura da página de serviços.
- **contato.html** 📧: Contém o formulário de contato e o script de consulta ao ViaCEP.
- **css/style.css** 🎨: Arquivo de estilo para o layout das páginas.
- **imagens/** 🖼️: Pasta contendo as imagens usadas no site.

## Como Funciona 🔧

### 1. **Página Inicial** 🏠

A página inicial é simples e direta, com um cabeçalho contendo o logo e um menu de navegação, que permite ao usuário acessar rapidamente as páginas de **Produtos**, **Serviços** e **Contato**.

O conteúdo principal da página apresenta uma breve introdução à empresa e seu foco em desenvolvimento web e serviços relacionados. O link para a página de **Serviços** também está visível, proporcionando fácil navegação.

### 2. **Página de Serviços** 🛠️

A página de serviços apresenta as principais áreas de atuação da empresa e uma galeria de imagens representando cada serviço. Ao clicar em uma imagem, o Lightbox exibe uma versão ampliada.

**Exemplo de código HTML da galeria de imagens:**
```html
<figure>
    <a href="imagens/desenvolvimento-web.jpg" title="web design" data-lightbox="galeria" data-title="Desenvolvimento Web">
        <img src="imagens/desenvolvimento-web-mini.jpg" alt="Desenvolvimento Web">
    </a>
    <a href="imagens/design-grafico.jpg" title="design gráfico" data-lightbox="galeria" data-title="Design Gráfico">
        <img src="imagens/design-grafico-mini.jpg" alt="Design Gráfico">
    </a>
    <a href="imagens/marketing-digital.jpg" title="Marketing Digital" data-lightbox="galeria" data-title="Marketing Digital">
        <img src="imagens/marketing-digital-mini.jpg" alt="Marketing Digital">
    </a>
    <a href="imagens/consultoria-treinamento.jpg" title="Consultoria e Treinamento" data-lightbox="galeria" data-title="Consultoria e Treinamento">
        <img src="imagens/consultoria-treinamento-mini.jpg" alt="Consultoria e Treinamento">
    </a>
</figure>
```

### 3. **Página de Contato** 📧

A página de contato contém um formulário onde os usuários podem enviar suas informações. Há campos para nome, e-mail, telefone, data de nascimento, CPF/CNPJ, e até um campo para inserir o CEP, que ao ser preenchido automaticamente preenche os campos de endereço com os dados obtidos da API ViaCEP.

**Exemplo de código para busca do CEP:**
```html
<script>
    // Função para buscar o endereço pela API do ViaCEP
    function buscarCEP() {
        const cep = document.getElementById('cep').value.replace(/\D/g, ''); // Remove caracteres não numéricos
        const status = document.getElementById('status');

        if (cep.length === 8) {
            status.textContent = 'Buscando endereço...';
            fetch(`https://viacep.com.br/ws/${cep}/json/`)
                .then(response => {
                    if (!response.ok) throw new Error('Erro na consulta do CEP');
                    return response.json();
                })
                .then(data => {
                    if (data.erro) {
                        throw new Error('CEP não encontrado');
                    }
                    document.getElementById('endereco').value = data.logradouro || '';
                    document.getElementById('bairro').value = data.bairro || '';
                    document.getElementById('cidade').value = data.localidade || '';
                    document.getElementById('estado').value = data.uf || '';
                    status.textContent = 'Endereço encontrado!';
                })
                .catch(error => {
                    status.textContent = error.message;
                });
        } else {
            status.textContent = 'CEP inválido.';
        }
    }
</script>
```

## Tecnologias Utilizadas 💻

- **HTML5** 📑: Para estruturar o conteúdo.
- **CSS3** 🎨: Para definir o estilo visual e layout responsivo.
- **JavaScript** 🖥️: Para interatividade, como a consulta ao ViaCEP e funcionalidade da galeria de imagens com Lightbox.
- **Lightbox2** 🖼️: Para exibir as imagens em tela cheia.
- **Formspree** 📧: Para enviar os dados do formulário de contato para um email.

## Como Utilizar 🚀

1. **Clone o Repositório**:
   Clone este repositório para sua máquina local:
   ```bash
   git clone https://github.com/seu-usuario/projeto-minimalix.git
   ```

2. **Abra os Arquivos**:
   Abra os arquivos HTML diretamente no seu navegador para visualizar as páginas **Home**, **Serviços** e **Contato**.

3. **Interaja com o Formulário**:
   Preencha o formulário na página de **Contato** e veja como o sistema busca automaticamente o endereço ao preencher o CEP.

## Licença 📜

Este projeto é de natureza didática, e pode ser utilizado para aprendizado e demonstrações. Direitos reservados a **Minimalix** para o conteúdo fictício apresentado.
