
# Configurando Appium Capabilities

Neste guia, você aprenderá como configurar as **Appium Capabilities** essenciais para se conectar ao servidor Appium e realizar automação de testes em um emulador Android.

## O que são Capabilities?

As **Capabilities** são configurações que informam ao Appium como ele deve iniciar e se conectar ao dispositivo ou emulador que você deseja testar. Elas são fundamentais para definir o ambiente de teste.

---

## Exemplo Básico de Configuração

Aqui está um exemplo de configuração mínima necessária para automação em um emulador Android:

```java
package br.com.utils;

import io.appium.java_client.android.options.UiAutomator2Options;

public class AppiumCapabilities {

    public static UiAutomator2Options appiumDesiredCapabilities() {
        UiAutomator2Options options = new UiAutomator2Options();
        options.setUdid("emulator-5554");
        options.setAppPackage("app.package");
        options.setAppActivity("br.com.app.activity.MainActivity");
        options.setAutomationName("UiAutomator2");
        options.setNoReset(false);

        return options;
    }
}
```

## Descrição das Principais Capabilities

| Nome              | Valor Exemplo                       | Descrição                                                                 |
|--------------------|-------------------------------------|---------------------------------------------------------------------------|
| udid              | "emulator-5554"                    | Identificador único do dispositivo ou emulador conectado via ADB.        |
| appPackage        | "app.package"                      | Define o pacote do aplicativo que será testado no dispositivo.           |
| appActivity       | "br.com.app.activity.MainActivity"  | Especifica a atividade principal do aplicativo que será iniciada.        |
| automationName    | "UiAutomator2"                     | Ferramenta de automação utilizada. UiAutomator2 é recomendada para Android. |
| noReset           | false                              | Indica se o estado do aplicativo será resetado entre os testes.          |

## Aplicando a inicialização do Appium Driver através de uma Hooks utilizando @Before

```java
package br.com.steps.hook;

import br.com.utils.AppiumCapabilities;
import io.appium.java_client.android.AndroidDriver;
import io.appium.java_client.service.local.AppiumDriverLocalService;
import io.appium.java_client.service.local.AppiumServiceBuilder;
import org.junit.After;
import org.junit.Before;

import java.time.Duration;

public class Hooks {
    public static AndroidDriver driver;

    @Before
    public void setUp() {
        iniciarAppiumDriver();
    }

    private void iniciarAppiumDriver() {
        AppiumServiceBuilder appiumServiceBuilder = new AppiumServiceBuilder()
                .usingPort(4723)
                .withIPAddress("127.0.0.1");
        AppiumDriverLocalService appiumService = AppiumDriverLocalService.buildService(appiumServiceBuilder);
        appiumService.start();
        driver = new AndroidDriver(appiumService.getUrl(), AppiumCapabilities.appiumDesiredCapabilities());
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(30));
    }

    @After
    public void tearDown() {
        if (driver != null) {
            driver.quit();
        }
    }
}
```

## Configurando o Servidor Appium

Certifique-se de que o servidor Appium está instalado e em execução.

Para iniciar o servidor:

```bash
appium
```

O servidor estará disponível no endereço padrão `http://127.0.0.1:4723`.

---

## Dicas para Iniciantes

- Sempre verifique se o emulador ou dispositivo está conectado com o comando:

```bash
adb devices
```

O retorno deve ser algo como:

```
emulator-5554 device
```

- `emulator-5554`: ID do emulador.
- `device`: Status (conectado).

Se o status retornar como "offline", pode ser uma lentidão na inicialização do emulador ou que o mesmo não está disponível para conexão.