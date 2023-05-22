<img src="https://cdn.discordapp.com/attachments/755000173922615336/1005601965897678979/banner.png" alt="KenaBot" />

**[Página principal](https://www.kenabot.xyz) - [Invitar al bot](https://www.kenabot.xyz/#bots) - [Términos y condiciones de servicio](https://www.kenabot.xyz/tos) - [Política de privacidad](https://www.kenabot.xyz/privacy) - [Equipo](https://www.kenabot.xyz/team) - [Contacto](mailto:admin@kenabot.xyz)**

```mermaid
graph TD

    PR[[AWS proxy]] <--> A

    API["REST API (api.kenabot.xyz)"] <--> RD
    IMG["Image server (img.kenabot.xyz)"]
    AUTH(["Auth server (auth.kenabot.xyz)"]) --> A

    DB1[("Database 1 (PROD)")] <-.-> A
    DB2[("Database 2 (STAGE)")] <-.-> DB1

    RD[(Cache server)] <--> B & C & D & E

    ARB[(Artist DB)] --> SP
    TDB[(Track DB)] --> SP 
    PDB[(Playlist DB)] --> SP
    SP([Spotify GC-1]) -->
    A(Protocol v2-dev) <--> B(KenaBot) --> NM
    A <--> C(KenaBot 2) --> NM
    A <--> D(KenaBot 3) --> NM
    A <--> E(KenaBot 4) --> NM

    A <--> API -.-> WEB["Web (kenabot.xyz)"]
    A --> IMG -.-> WEB

    N1["Atenea 1 (us-south)"]
    N2["Atenea 2 (us-west)"]
    N3["Atenea 3 (eu-central-1)"]
    N4["Atenea 4 (eu-central-2)"]
    N5["Atenea 5 (sa-east-1)"]
    N6["Atenea 6 (sa-east-2)"]
    N7["Atenea 7 (madrid-1)"]

    NM[Atenea load-balancer]

    NM --> N1 & N2 & N3 & N4 & N5 & N6 & N7
```
