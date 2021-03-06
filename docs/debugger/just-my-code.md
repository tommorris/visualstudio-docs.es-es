---
title: Depurar el código de usuario con sólo mi código | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a2873f691fdaa1251a5562e21e2bbd0467eb2e2
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612758"
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Especifique si desea depurar el código de usuario sólo con sólo mi código en Visual Studio
Puede configurar Visual Studio para automáticamente paso a través del sistema, framework y otras llamadas que no son de usuario y contraer esas llamadas en la ventana Pila de llamadas. La característica que habilita o deshabilita este comportamiento se denomina *solo mi código*. Este tema describe cómo usar solo mi código en proyectos de C#, Visual Basic, C++ y JavaScript.

Para la mayoría de los lenguajes de programación, solo mi código está habilitada de forma predeterminada.
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Habilitar o deshabilitar solo mi código  
 Para habilitar o deshabilitar solo mi código, elija el **Herramientas > opciones** menú en Visual Studio. En el **depuración** > **General** nodo, elija o borre **habilitar solo mi código**.
  
 ![Habilitar Solo mi código en el cuadro de diálogo Opciones](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  El **habilitar solo mi código** configuración es una configuración global que se aplica a todos los proyectos de Visual Studio en todos los idiomas.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Mostrar código de no usuario en las vistas de pila de llamadas  
 En las vistas que muestran la pila de llamadas, como el **pila de llamadas** y **tareas** windows, solo mi código contrae el código de no usuario en un marco anotado con la etiqueta `[External Code]`. Para ver los marcos contraídos, elija **mostrar código externo** en el menú contextual de la pila de llamadas Mostrar.

 ![Mostrar código externo en la ventana Pila de llamadas](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  El **mostrar código externo** configuración se guarda en el generador de perfiles del usuario actual. Se aplica a todos los proyectos en todos los lenguajes abiertos por el usuario.

##  <a name="identify-user-code-while-debugging"></a>Identificar el código de usuario durante la depuración 

El **módulos** ventana puede indicarle qué módulos de código, el depurador es tratar como código de usuario, o mi código, junto con información como el símbolo de estado para el módulo de carga. Para obtener más información, consulte [familiarizarse más con cómo el depurador se asocia a la aplicación](../debugger/debugger-tips-and-tricks.md#modules_window).
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> Solo mi código de .NET framework  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Código de usuario y no de usuario  
 Para diferenciar el código de usuario de código de no usuario, solo mi código examina los archivos de símbolos (.pdb) y las optimizaciones de programa. El depurador considera el código como código que no es de usuario cuando se optimiza el archivo binario o cuando el archivo .pdb no está disponible.
  
 Hay tres atributos que también afectan a lo que el depurador considera ser Mi código:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al depurador que el código al que se aplica no es Mi código.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta el código para el depurador, incluso si Solo mi código está desactivado.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al depurador que recorra el código al que se aplica en lugar de ejecutarlo paso a paso por instrucciones.  
  
 El código restante se considera código de usuario.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Comportamiento de ejecución paso a paso  
 Cuando se **paso a paso** (método abreviado de teclado: F11) código de no usuario, el depurador salta el código a la siguiente instrucción del usuario. Cuando se **paso a paso fuera** (teclado: MAYÚS + F11), el depurador ejecuta hasta la siguiente línea de código de usuario. Si no se encuentra ningún código de usuario, la ejecución continúa hasta que la aplicación se cierra, un punto de interrupción o se produce una excepción.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Comportamiento de punto de interrupción  
 Cuando está habilitado solo mi código, puede elegir **interrumpir todos** (teclado: Ctrl + Alt + Inter) y detener la ejecución en una ubicación donde no hay ningún código de usuario para mostrar. Cuando esto sucede, se muestra la ventana No hay código fuente. Si se elige un comando Paso, el depurador le lleva a la línea siguiente de código de usuario.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Comportamiento de excepción  
 Si se produce una excepción no controlada en código que no es de usuario, el depurador interrumpe la ejecución en la línea del código de usuario donde se generó la excepción.  
  
 Si se han habilitado excepciones de primera aparición para la excepción, la línea de código de usuario se resalta en color verde. La pila de llamadas muestra un marco anotado con la etiqueta **[código externo]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> Solo mi código de C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Código de usuario y no de usuario  
Solo mi código de C++ es diferente de Solo mi código de .NET Framework y JavaScript porque el comportamiento de ejecución paso a paso es independiente del comportamiento de la pila de llamadas.  

A partir de 15,8 de Visual Studio 2017, puede especificar si desea habilitar solo mi código para el uso de C++ **herramientas** > **opciones** > **depuración**  >  **General** > **habilitar solo mi código** (está habilitado de forma predeterminada). Esto es equivalente a usar el [/JMC (solo mi código de depuración)](/cpp/build/reference/jmc) modificador del compilador.
  
 **Pilas de llamadas**  
  
 De forma predeterminada, el depurador considera que estas funciones son código que no es de usuario las en ventanas Pila de llamadas:  
  
-   Funciones con información de origen eliminada en su archivo de símbolos.  
  
-   Funciones en las que los archivos de símbolos indican que no hay ningún archivo de código fuente correspondiente al marco de pila.  
  
-   Funciones especificadas en archivos `*.natjmc` en la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
 **Ejecución paso a paso**  
  
 De forma predeterminada, solo las funciones especificadas en archivos `*.natstepfilter` en la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` se consideran código que no es de usuario.  
  
 Puede crear sus propios archivos `.natstepfilter` y `.natjmc` para personalizar el comportamiento de ejecución paso a paso y de la ventana Pila de llamadas en `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Comportamiento de ejecución paso a paso  
 Cuando se **paso a paso** (método abreviado de teclado: F11) código de no usuario desde el código de usuario, el depurador salta el código hasta la siguiente línea de código de usuario. Cuando se **paso a paso fuera** (teclado: MAYÚS + F11), el depurador ejecuta hasta la siguiente línea de código de usuario. Si no se encuentra ningún código de usuario, la ejecución continúa hasta que la aplicación se cierra, un punto de interrupción o se produce una excepción.  
  
 Si el depurador interrumpe la ejecución en código que no es de usuario (por ejemplo, si un comando Interrumpir todos se detiene en código que no es de usuario), la ejecución paso a paso continúa en el código que no es de usuario.
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Comportamiento de excepción  
 Cuando el depurador llega a una excepción, se detiene en la excepción independientemente de si es de usuario o el código que no es de usuario. El **User-unhandled** opciones en el **excepciones** se pasan por alto el cuadro de diálogo.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizar el comportamiento de ejecución paso a paso  
 Puede especificar que se salten funciones si las enumera como código que no es de usuario en archivos `*.natstepfilter`.  
  
-   Para especificar código que no son de usuario para todos los usuarios del equipo de Visual Studio, agregue el archivo .natstepfilter a la `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` carpeta.  
  
-   Para especificar código que no son de usuario para un usuario individual, agregue el archivo .natstepfilter a la `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` carpeta.  
  
 Los archivos .natstepfilter son archivos XML con esta sintaxis:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Función|Requerido. Especifica una o más funciones como funciones que no son de usuario.|  
|`Name`|Requerido. Expresión regular con formato ECMA-262 que especifica el nombre de función completo que debe coincidir. Por ejemplo:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al depurador que todos los métodos de `MyNS::MyClass` deben considerarse código que no es de usuario. La coincidencia distingue mayúsculas de minúsculas.|  
|`Module`|Opcional. Expresión regular con formato ECMA-262 que especifica la ruta de acceso completa al módulo que contiene la función. La búsqueda no distingue entre mayúsculas y minúsculas.|  
|`Action`|Requerido. Uno de estos valores que distingue mayúsculas y minúsculas:<br /><br /> -   `NoStepInto`  -indica al depurador que omita la función coincidente.<br />-   `StepInto`  -indica al depurador paso a paso por las funciones coincidentes, invalidando cualquier otro `NoStepInto` para las funciones coincidentes.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizar el comportamiento de la pila de llamadas  
 Se puede especificar que se trate como código que no es de usuario módulos, archivos de código fuente y funciones en las pilas de llamadas; para ello, hay que especificarlos en archivos `*.natjmc`.  
  
-   Para especificar código que no son de usuario para todos los usuarios del equipo de Visual Studio, agregue el archivo .natjmc a la `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` carpeta.  
  
-   Para especificar código que no son de usuario para un usuario individual, agregue el archivo .natjmc a la `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` carpeta.  
  
 Los archivos .natjmc son archivos XML con esta sintaxis:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Atributos del elemento Module**  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. Ruta de acceso completa al módulo o los módulos. Puede usar los caracteres comodín de Windows `?` (cero o un carácter) y `*` (cero o más caracteres). Por ejemplo,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indica al depurador que trate como código externo todos los módulos de `\3rdParty\UtilLibs` en cualquier unidad.|  
|`Company`|Opcional. Nombre de la compañía que publica el módulo que está incrustado en el archivo ejecutable. Puede utilizar este atributo para eliminar la ambigüedad de los módulos.|  
  
 **Atributos del elemento File**  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. Ruta de acceso completa del archivo o archivos de código fuente que se van a tratar como código externo. Puede usar los caracteres comodín `?` y `*` de Windows para especificar la ruta de acceso.|  
  
 **Atributos del elemento Function**  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. Nombre completo de la función que se va a tratar como código externo.|  
|`Module`|Opcional. Nombre o ruta de acceso completa al módulo que contiene la función. Puede utilizar este atributo para eliminar la ambigüedad de funciones que tienen el mismo nombre.|  
|`ExceptionImplementation`|Cuando se establece en `true`, la pila de llamadas muestra la función que produjo la excepción en lugar de esta función.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Solo mi código de JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Código de usuario y no de usuario  
 **Clasificaciones de código**  
  
 Solo mi código de JavaScript controla la ejecución paso a paso y la presentación de la pila de llamadas categorizando el código en una de estas clasificaciones:  
  
|||  
|-|-|  
|**MyCode**|Código de usuario que posee y controla.|  
|**LibraryCode**|Código que no es de usuario de bibliotecas que utiliza con frecuencia y que la aplicación necesita para funcionar correctamente (por ejemplo, WinJS o jQuery).|  
|**UnrelatedCode**|Código de no usuario podría ejecutarse en su aplicación, pero no su propietario y la aplicación no depende directamente para que funcione correctamente. (Por ejemplo, esto podría incluir un SDK que muestra anuncios publicitarios.) En los proyectos UWP, cualquier código que se carga en la aplicación desde un URI HTTP o HTTPS también se considera UnrelatedCode.|  
  
 El depurador de JavaScript clasifica automáticamente estos tipos de código:  
  
-   Secuencia de comandos que se ejecuta pasando una cadena a la proporcionada por el host `eval` función se clasifica como **MyCode**.  
  
-   Secuencia de comandos que se ejecuta pasando una cadena a la `Function` constructor se clasifica como **LibraryCode**.  
  
-   Secuencia de comandos que se encuentra en una referencia de framework, como WinJS o el SDK de Azure, se clasifica como **LibraryCode**.  
  
-   Secuencia de comandos que se ejecuta pasando una cadena a la `setTimeout`, `setImmediate`, o `setInterval` funciones se clasifica como **UnrelatedCode**.  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` especifica otro usuario y código que no es de usuario para todos los proyectos de JavaScript de Visual Studio.  
  
 Es posible modificar las clasificaciones predeterminadas y clasificar determinados archivos y direcciones URL si se agrega un archivo .json denominado `mycode.json` a la carpeta raíz de un proyecto.  
  
 El código restante se clasifica como **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Comportamiento de ejecución paso a paso  
  
-   Si una función no es de usuario (**MyCode**) código, **paso a paso** (método abreviado de teclado: F11) se comporta como **saltar** (teclado: F10).  
  
-   Si un paso comienza en el que no es de usuario (**LibraryCode** o **UnrelatedCode**) de código, a continuación, la ejecución paso a paso temporalmente se comporta como si no está habilitado solo mi código. Cuando se pasa al código de usuario, solo mi código se vuelve a habilitar la ejecución paso a paso.  
  
-   Cuando un paso en código de usuario hace que se salga del contexto de ejecución actual (como un paso en la última línea de un controlador de eventos), el depurador se detiene en la siguiente línea de código de usuario ejecutada. Por ejemplo, si se ejecuta en una devolución de llamada **LibraryCode** código el depurador continúa hasta que se ejecuta la siguiente línea de código de usuario.
  
-   **Paso a paso fuera** (teclado: MAYÚS + F11) se detiene en la siguiente línea de código de usuario. Si no se encuentra ningún código de usuario, la ejecución continúa hasta que la aplicación se cierra, un punto de interrupción o se produce una excepción.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Comportamiento de punto de interrupción  
  
-   Puntos de interrupción establecidos en el código siempre se tendrán en cuenta, independientemente de la clasificación de ese código  
  
-   Si se encuentra la palabra clave `debugger` en:  
  
    -   **LibraryCode** código, el depurador siempre interrumpe.  
  
    -   **UnrelatedCode** código, no se detiene el depurador.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Comportamiento de excepción  
 Si se produce una excepción no controlada en:  
  
-   **MyCode** o **LibraryCode** código, el depurador siempre interrumpe.  
  
-   **UnrelatedCode** código, y **MyCode** o **LibraryCode** código se encuentra en la pila de llamadas, el depurador se interrumpa.  
  
 Si se habilitan excepciones de primera oportunidad para la excepción en el cuadro de diálogo de excepciones y se produce la excepción **LibraryCode** o **UnrelatedCode** código:  
  
-   Si se controla la excepción, no se interrumpe el depurador.  
  
-   Si la excepción no se controla, se interrumpe el depurador.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizar solo mi código  
 Para categorizar el código de usuario y el código que no es de usuario para un único proyecto de Visual Studio, agregue un archivo .json denominado `mycode.json` a la carpeta raíz del proyecto.  
  
 Las clasificaciones se realizan en este orden:  
  
1.  Clasificaciones predeterminadas  
  
2.  Clasificaciones en el archivo `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`  
  
3.  Clasificaciones en el archivo `mycode. json` del proyecto actual.  
  
 Cada paso de clasificación invalida los pasos anteriores. No necesita un archivo .json enumerar todos los pares clave / valor y el **MyCode**, **bibliotecas**, y **Unrelated** valores pueden ser matrices vacías.  
  
 Los archivos .json de Mi código utilizan esta sintaxis:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec",  
        . .  
        "UrlOrFileSpec"  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ]  
}  
  
```  
  
 **Eval, Function y ScriptBlock**  
  
 El **Eval**, **función**, y **ScriptBlock** pares clave / valor determinar cómo dinámicamente se clasifica el código generado.  
  
|||  
|-|-|  
|**Eval**|Script que se ejecuta pasando una cadena a la función `eval` proporcionada por el host. De forma predeterminada, el script Eval se clasifica como **MyCode**.|  
|**Function**|Script que se ejecuta pasando una cadena al constructor de `Function`. De forma predeterminada, el script Function se clasifica como **LibraryCode**.|  
|**Bloque de script**|Script que se ejecuta pasando una cadena a las funciones `setTimeout`, `setImmediate` o `setInterval`. De forma predeterminada, el script ScriptBlock se clasifica como **UnrelatedCode**.|  
  
 Puede cambiar el valor a una de estas palabras clave:  
  
-   `MyCode`  clasifica el script como **MyCode**.  
  
-   `Library`  clasifica el script como **LibraryCode**.  
  
-   `Unrelated`  clasifica el script como **UnrelatedCode**.  
  
 **MyCode, Libraries y Unrelated**  
  
 El **MyCode**, **bibliotecas**, y **Unrelated** pares clave / valor que especifique las direcciones URL o archivos que se van a incluir en una clasificación:  
  
|||  
|-|-|  
|**MyCode**|Una matriz de direcciones URL o archivos que se clasifican como **MyCode**.|  
|**Bibliotecas**|Una matriz de direcciones URL o archivos que se clasifican como **LibraryCode**.|  
|**No relacionados**|Una matriz de direcciones URL o archivos que se clasifican como **UnrelatedCode**.|  
  
 La dirección URL o la cadena de archivo puede contener uno o más caracteres `*`, que coinciden con cero o más caracteres. `*` es el equivalente de la expresión regular `.*`.
