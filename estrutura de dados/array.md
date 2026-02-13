```mermaid
flowchart TD
    A[Estruturas de Dados] 
    A --->B[tipos de dados]
    A ---> C[Foco em organização]
    A ----> Ar[arrays] 
    Ar --> D[vetores]
    Ar --> M[matrizes]
    M ----> D4a 
 
    B -.-> T[tipo de dados abstratos]
    
    D --> D1[estatiticos] --> D2[tamanho definido] --> D4a[indexavel]
    D --> D3[dinamico] --> D4[tamanho variavel] --> D4a[indexavel]
    D --> D5[unidimensional e homogenio]
	
	M --> MB[Bi-dimensional] 
	MB --> MB1[pode se imaginar como uma planilha com linhas e colunas]
    
	
 

