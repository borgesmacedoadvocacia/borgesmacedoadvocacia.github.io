# Central de Dashboards — Borges Macedo Advocacia

Ponto único de acesso a todos os dashboards do escritório:
**https://borgesmacedoadvocacia.github.io/**

- Login único (a lista de dashboards fica cifrada com AES-256-GCM; a chave é
  derivada do login + senha via PBKDF2-SHA256 com 310.000 iterações — senha
  errada não decifra nada).
- Menu lateral com os dashboards agrupados por área (Comercial, Processual,
  Financeiro); o dashboard escolhido abre na área principal da tela.
- Os links antigos de cada dashboard redirecionam para esta central.
- A sessão vale para a aba atual e termina ao fechá-la.

Os dashboards continuam hospedados nos seus repositórios de origem e são
exibidos dentro da central. Por estarem na mesma origem (`github.io`), a
sessão da central destrava automaticamente os dashboards protegidos por
cofre, sem novo login.
