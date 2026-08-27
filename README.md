# Central de Dashboards — Borges Macedo Advocacia

Ponto único de acesso a todos os dashboards do escritório:
**https://borgesmacedoadvocacia.github.io/**

## Perfis de acesso

Cada perfil tem o seu próprio cofre (AES-256-GCM; chave derivada do login +
senha via PBKDF2-SHA256 com 310.000 iterações). O login testa os cofres e o
que a senha decifrar define o menu — um perfil não tem como decifrar o menu
do outro, e senha errada não decifra nada.

| Perfil | Acesso |
|---|---|
| Administração | Todos os dashboards |
| Lideranças | Todos os dashboards |
| Equipe | Metas e Resultados — Comercial e Metas e Resultados — Processual |

Os dashboards protegidos por cofre próprio (Fluxo Financeiro, Metas
Processual, Execuções) têm um cofre **por perfil autorizado**: a credencial
da Equipe não decifra o Fluxo Financeiro nem as Execuções em hipótese
alguma — não é só o menu que esconde, é a criptografia que barra. Os
dashboards sem cofre próprio ficam protegidos pelo redirecionamento para a
central e pela ausência no menu do perfil.

O nome de usuário aceita acentos e caixa livre ("Lideranças", "liderancas"
e "LIDERANÇAS" valem igual). As senhas não ficam documentadas aqui.

## Funcionamento

- Menu lateral com os dashboards agrupados por área (Comercial, Processual,
  Financeiro); o dashboard escolhido abre na área principal da tela.
- Os links antigos de cada dashboard redirecionam para esta central.
- A sessão vale para a aba atual e termina ao fechá-la.

Os dashboards continuam hospedados nos seus repositórios de origem e são
exibidos dentro da central. Por estarem na mesma origem (`github.io`), a
sessão da central destrava automaticamente os dashboards protegidos por
cofre que o perfil logado pode ver, sem novo login.
