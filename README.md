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
| Administração | Todos os 15 dashboards |
| Lideranças | Todos os 15 dashboards, incluindo o **Ambiente do CEO** e os cinco exclusivos (Alvarás e Acordos, Base de Clientes, CRM Jurídico, Diligências e Controladoria Jurídica) |
| Equipe | Metas e Resultados — Comercial, Metas e Resultados — Processual e Dados do Kommo |

Os dashboards protegidos por cofre próprio (Fluxo Financeiro, Metas
Processual, Execuções e os cinco exclusivos das lideranças) têm um cofre
**por perfil autorizado**: a credencial da Equipe não decifra o Fluxo
Financeiro, as Execuções nem qualquer painel exclusivo em hipótese alguma —
não é só o menu que esconde, é a criptografia que barra. Os dashboards sem
cofre próprio ficam protegidos pelo redirecionamento para a central e pela
ausência no menu do perfil.

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

## Incluir um dashboard no menu

O menu de cada perfil vive dentro do cofre daquele perfil — para acrescentar um
painel é preciso reabrir o cofre, inserir o item e refazê-lo. A ferramenta
[`atualizar-menu.html`](https://borgesmacedoadvocacia.github.io/atualizar-menu.html)
faz isso **no próprio navegador**: a senha nunca sai da máquina e nunca é gravada.

1. Preencha grupo, id, nome e URL do dashboard.
2. Para cada perfil que deve enxergá-lo: usuário + senha › *Incluir e refazer o cofre*.
3. Perfis que **não** devem vê-lo: *Este perfil não deve ver o painel* (o cofre fica intacto).
4. Copie o bloco `const COFRES = [ … ];` gerado e substitua o do `index.html`.

O `atualizar-menu.html` guarda uma cópia dos cofres — depois de trocar o
`index.html`, atualize também a cópia dentro dele.
