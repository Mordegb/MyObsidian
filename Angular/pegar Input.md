
#### para pegar valores de Input no angular, no seu arquivo <span style="color:rgb(0, 112, 192)">.ts</span>  você deve fazer o import do FormsModule ``` import { FormsModule } from '@angular/forms';``` e criar criar as variáveis para oque vc quer fazer. Nun exemplo de tela de login temos:

```
UserEmail:string = ''
UserPassword:string = ''
```
#### com as variáveis criadas você deve dizer ao seus inputs do <span style="color:rgb(255, 77, 0)">.html</span>  as variáveis que vai receber os valores dos input usando o [(ngModel)].

```
<input type="text" placeholder="email" name="email" [(ngModel)]="UserEmail">
<input type="pasword" placeholder="Senha" name="email"[(ngModel)]="UserPassword"
```
#### no [(ngModel)] você colocar entre parenteses o nome da variável que vai receber o valor do input.

#### toda vez que usar o ng model vc dever dar um nome do input, assim como aparece no exemplo acima, confia em mim se não tiver esse *<span style="color:rgb(255, 0, 0)">name=""</span> , da ruim é serio. 