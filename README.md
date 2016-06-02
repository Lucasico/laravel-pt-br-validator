#Laravel 5 - Validação em Português

**Atenção**: Por motivo de melhor organização dos projetos escritos para Laravel, essa biblioteca agora passa a parar de receber atualizações nesse repositório. Alternativamente, você deve usar esse:

https://github.com/LaravelLegends/pt-br-validator




Essa é uma biblioteca com algumas validações brasileiras.


#Instalação

No arquivo `composer.json`, adicione:

```json
{
	"phplegends/pt-br-validator" : "2.*"
}
```

Rode o comando `composer update --no-scripts`.

Após a instalação, adicione no arquivo `config/app.php` a seguinte linha:

```php

PHPLegends\PtBrValidator\ValidatorProvider::class

```

Para utilizar a validação agora, basta fazer o procedimento padrão do `Laravel`.

A diferença é que agora, você terá os seguintes métodos de validação:

* celular - Valida um celular através do formato 99999-9999 ou 9999-9999

* celular_com_ddd -  Valida um celular através do formato (99)99999-9999 ou (99)9999-9999

* cnpj - Valida se o CNPJ é valido. Para testar, basta utilizar o site http://www.geradorcnpj.com/

* cpf - Valida se o cpf é valido. Para testar, basta utilizar o site http://geradordecpf.
org

* data - Valida se a data está no formato 31/12/1969

* formato_cnpj - Valida se a mascará do CNPJ é válida

* formato_cpf - Valida se a mascará do cpf está certo. 999.999.999-99

* telefone - Valida um telefone através do formato 9999-9999

* telefone_com_ddd - Valida um telefone através do formato (99)9999-9999


Então, podemos usar um simples teste:


```php
$validator = Validator::make(
	['telefone' => '(77)9999-3333'],
	['telefone' => 'required|telefone_com_ddd']
);

dd($validator->fails());

```


Já existe nessa biblioteca algumas mensagens padrão para as validações de cada um dos items citados acima. 

Para modificar isso, basta adicionar ao terceiro parâmetro de `Validator::make` um array, contendo o índice com o nome da validação e o valor com a mensagem desejada.


Exemplo:


```php
Validator::make($valor, $regras, ['celular_com_ddd' => 'O campo :attribute não é um celular'])
```

