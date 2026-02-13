- fast API / flask
- mySQL
- SLQlite
- comunicação API banco de dados

```mermaid
flowchart LR

	A[Python basico]
	A --> a1[FastAPI] 
	A --> a2[Flask]
	
	a1 --> s[SLQl puro] --> ps[postgres]
	a2 --> s
	
	s --> sq{{SQL-archemy}}
	s --> SQ[SQL lite] 
	sq --> r[flask + SQL-archemy]
	
	
	B[bando de dados] --> ap[API] -->c[codigo]
	ap --> B
	


