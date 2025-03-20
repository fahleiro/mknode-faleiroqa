
# APPIUM SERVER

## Instalação Usando `npm`

Para instalar o Appium Server globalmente no seu sistema, use o seguinte comando no terminal:

```bash
npm install -g appium
```

Após a instalação, você pode verificar se o Appium foi instalado corretamente rodando:

```bash
appium --version
```

## Como Iniciar o Servidor

Para iniciar o Appium Server, utilize o comando:

```bash
appium
```

Por padrão, o servidor será iniciado no IP `0.0.0.0` (todas as interfaces de rede disponíveis) e na porta `4723`.

Você pode personalizar o IP e a porta com o seguinte comando:

```bash
appium --address <IP_DESEJADO> --port <PORTA_DESEJADA>
```

Por exemplo:

```bash
appium --address 192.168.0.18 --port 4723
```

## Plugins Essenciais

Para automação em iOS e Android, você precisará instalar os seguintes plugins do Appium:

### iOS: Plugin `xcuitest`

1. Instale o plugin com o comando:
   ```bash
   appium plugin install --plugin xcuitest
   ```

2. Para verificar se o plugin foi instalado corretamente:
   ```bash
   appium plugin list
   ```

### Android: Plugin `uiautomator2`

1. Instale o plugin com o comando:
   ```bash
   appium plugin install --plugin uiautomator2
   ```

2. Verifique a instalação:
   ```bash
   appium plugin list
   ```

## Notas Importantes

- **IP e Porta**:
  - Certifique-se de que o IP configurado no Appium Server seja acessível pelo dispositivo ou emulador que você está utilizando.
  - A porta padrão é `4723`, mas você pode alterá-la para evitar conflitos com outros serviços.

- **XCUITest e UIAutomator2**:
  - Esses plugins são essenciais para automação em dispositivos reais e emuladores.
  - Para iOS, você precisa de um sistema macOS com Xcode instalado.
  - Para Android, assegure-se de que o Android SDK esteja configurado corretamente e que o dispositivo tenha o modo de depuração ativado.

## Alternativa ao `npm`
Outra opção é utilizar o [Appium Desktop](https://github.com/appium/appium-desktop), disponível para Mac, Windows e Linux. Essa ferramenta oferece uma interface mais intuitiva, tornando o processo de configuração do IP e da porta mais acessível e amigável, sem perder a flexibilidade das configurações tradicionais.

<script type="text/javascript">
	atOptions = {
		'key' : '71a1dd532287ae867038be06f4a24109',
		'format' : 'iframe',
		'height' : 60,
		'width' : 468,
		'params' : {}
	};
</script>
<script type="text/javascript" src="//www.highperformanceformat.com/71a1dd532287ae867038be06f4a24109/invoke.js"></script>