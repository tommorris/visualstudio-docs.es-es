---
title: Especificar archivos de código fuente y símbolos (.pdb) en el depurador | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/05/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9167970030919073bf5a58ccf7368cff69dc896
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612745"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio
Un archivo de base de datos (.pdb) del programa, también denominado archivo de símbolos, asigna los identificadores que se crean en el código fuente para las clases, métodos y otros códigos para los identificadores que se usan en los ejecutables compilados del proyecto. El archivo .pdb también asigna las instrucciones del código fuente a las instrucciones de ejecución de los archivos ejecutables. El depurador utiliza estos datos para determinar dos elementos clave de la información:

* Nombre del número de archivo y la línea de código fuente que se mostrará en el IDE de Visual Studio
* Ubicación del archivo ejecutable para detenerse cuando se establece un punto de interrupción

Un archivo de símbolos también contiene la ubicación original de los archivos de código fuente y, opcionalmente, la ubicación de un servidor de origen en donde pueden recuperarse los archivos de código fuente.
  
> [!TIP]
> Si desea depurar el código fuera de su código fuente del proyecto, como código de Windows o third party code llame el proyecto, tendrá que especificar la ubicación de los .pdb (y, opcionalmente, los archivos de origen del código externo) y los archivos deben coincidir exactamente con la compilación de t que los archivos ejecutables. 

##  <a name="how-can-i-manage-symbol-files-while-debugging"></a>¿Cómo se puede administrar los archivos de símbolos durante la depuración? 

El **módulos** ventana puede indicarle qué módulos de código, el depurador está tratando como código de usuario, o mi código y el símbolo de estado para el módulo de carga. También puede usar esta ventana para cargar símbolos durante la depuración. Para obtener más información, consulte [familiarizarse más con cómo el depurador se asocia a la aplicación](../debugger/debugger-tips-and-tricks.md#modules_window).
 
##  <a name="BKMK_Find_symbol___pdb__files"></a> ¿Donde el depurador busca archivos de símbolos? 
  
1.  La ubicación que se especifica dentro del archivo DLL o el archivo ejecutable.  
  
     (De forma predeterminada, si ha compilado una DLL o un archivo ejecutable en su equipo, el vinculador coloca la ruta de acceso completa y el nombre del archivo .pdb asociado dentro de la DLL o el archivo ejecutable. El depurador comprueba primero si el archivo de símbolos existe en la ubicación especificada dentro del archivo DLL o el archivo ejecutable. Esto resulta útil, porque siempre hay símbolos disponibles para el código que ha compilado en el equipo).  
  
2.  archivos .pdb que se encuentran en la misma carpeta que el archivo DLL o un archivo ejecutable.

3. Todas las ubicaciones [especificado en las opciones del depurador](#BKMK_Specify_symbol_locations_and_loading_behavior) archivos de símbolos. 
  
    * Cualquier carpeta de caché de símbolos local.  
  
    * Cualquier red, internet, o servidores de símbolos local y ubicaciones que se especifiquen, por ejemplo, el servidor de símbolos de Microsoft (si está habilitado). 

> [!NOTE]
> Antes de Visual Studio 2012, para depurar código administrado en un dispositivo remoto, era necesario colocar los archivos de símbolos en el equipo remoto. A partir de Visual Studio 2012, todos los archivos de símbolos deben encontrarse en el equipo local o en una ubicación [especificado en las opciones del depurador](#BKMK_Specify_symbol_locations_and_loading_behavior).  
  
##  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> ¿Por qué los archivos de símbolos deben coincidir exactamente con los archivos ejecutables?  
El depurador solo cargará un archivo .pdb de un archivo ejecutable que coincida exactamente con el archivo .pdb creado cuando se compiló el archivo ejecutable (es decir, el archivo .pdb debe ser el original o una copia del archivo .pdb original). Dado que el compilador está optimizado para acelerar la compilación además de su tarea principal de crear un código correcto y eficaz, el diseño real de un archivo ejecutable puede cambiar aunque el propio código no haya cambiado. Para obtener más información, consulte [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)
  
##  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Configurar donde el depurador busca archivos de símbolos y el comportamiento de carga de símbolos
 Cuando se depura un proyecto en el IDE de Visual Studio, el depurador carga automáticamente los archivos de símbolos que se encuentran en el directorio del proyecto. Puede especificar rutas de acceso de búsqueda alternativas y servidores de símbolos de Microsoft, Windows o componentes de terceros en **Herramientas > Opciones > depuración > símbolos**. También puede especificar módulos concretos que quiere que el depurador cargue símbolos automáticamente. Y posteriormente puede cambiar esta configuración manualmente mientras está depurando de manera activa.  
  
1.  En Visual Studio, abra el **Herramientas > Opciones > depuración > símbolos** página.  
  
     ![Herramientas &#45; opciones &#45; depuración &#45; página símbolos](../debugger/media/dbg_tools_options_symbols.gif "DBG_Tools_Options_Symbols")  
  
2.  Elija la carpeta ![herramientas&#47; opciones&#47; depuración&#47;icono de carpeta Symbols](../debugger/media/dbg_tools_options_foldersicon.png "DBG_Tools_Options_FoldersIcon") icono. En el cuadro **Ubicaciones del archivo de símbolos (.pdb)** , aparece texto modificable.  
  
3.  Escriba la dirección URL o la ruta de acceso del directorio del servidor de símbolos o de la ubicación del símbolo. La finalización de instrucciones le será de ayuda para especificar el formato correcto.

    Puede usar **Ctrl+flecha arriba** y **Ctrl+flecha abajo** para cambiar el orden de carga para las ubicaciones de símbolos. Presione **F2** para editar una dirección URL o ruta de acceso de directorio.
  
4.  Para mejorar el rendimiento de carga de los símbolos, escriba la ruta de acceso de un directorio local en el que los servidores de símbolos puedan copiar los símbolos en el cuadro **Almacenar en caché los símbolos de este directorio** .  
  
    > [!NOTE]
    >  No coloque la memoria caché de símbolos en una carpeta protegida (como la carpeta C:\Windows o una de sus subcarpetas). Utilice una carpeta de lectura y escritura en su lugar.  
  
    > [!NOTE]
    >  Para los proyectos de C++, si tiene el conjunto de variables de entorno _NT_SYMBOL_PATH, reemplazará el valor establecido en **almacenar en caché los símbolos de este directorio**.

### <a name="specify-symbol-loading-behavior"></a>Especificar el comportamiento de carga de los símbolos 
  
Puede especificar los archivos que desea cargar automáticamente desde ubicaciones del cuadro **Ubicaciones de archivos de símbolos (.pdb)** cuando inicie la depuración. Los archivos de símbolos del directorio del proyecto siempre se cargan.  
  
1.  Elija **Todos los módulos, excepto los excluidos** para cargar todos los símbolos de todos los módulos excepto los que especifique si elige el vínculo **Especificar módulos excluidos** .  
  
2.  Elija la opción **Solo los módulos especificados** y, a continuación, seleccione **Especificar módulos** para enumerar los archivos de símbolos de los módulos que desee cargar automáticamente. Los archivos de símbolos de otros módulos se omiten.  
  
### <a name="specify-additional-symbol-options"></a>Especificar opciones de símbolos adicionales 
  
También puede establecer las siguientes opciones en el **Herramientas > Opciones > depuración > General** página:  
  
**Cargar exportaciones de DLL (solo nativo)**  
  
Cuando se selecciona esta opción, se cargan las tablas de exportación de archivos DLL. La información simbólica de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, cálculo de referencias o cualquier archivo DLL para el que no disponga de símbolos. La lectura de la información de exportación de archivos DLL implica cierta sobrecarga. Por lo tanto, esta funcionalidad está desactivada de forma predeterminada.  
  
Para ver los símbolos que están disponibles en la tabla de exportación de un archivo DLL, utilice `dumpbin /exports`. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Si lee el resultado de `dumpbin /exports` , podrá ver el nombre exacto de la función, incluidos los caracteres no alfanuméricos. Esto resulta útil para establecer un punto de interrupción en una función. Los nombres de función procedentes de tablas de exportación de archivos DLL pueden aparecer truncados en otras partes del depurador. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Usar servidores de símbolos para buscar archivos de símbolos que no estén en el equipo local  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede descargar archivos de símbolos de depuración de servidores de símbolos que implementan el protocolo symsrv. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/Library/bd6977ca-e30a-491a-a153-671d81222ce6) y las [Herramientas de depuración para Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) son dos herramientas que pueden implementar servidores de símbolos. Especifique los servidores de símbolos que desee usar en el cuadro **Opciones** de VS.  
  
 Los servidores de símbolos que podría utilizar incluyen:  
  
 **Servidores de símbolos públicos de Microsoft**  
  
 Para depurar un bloqueo que se produzca durante una llamada a un archivo DLL del sistema o a una biblioteca de terceros, generalmente necesitará archivos .pdb del sistema, que contienen símbolos de archivos DLL, EXE y controladores de dispositivos de Windows. Puede obtener estos símbolos en los servidores de símbolos públicos de Microsoft. Los servidores de símbolos públicos de Microsoft proporcionan símbolos de los sistemas operativos Windows, además de MDAC, IIS, ISA y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Para utilizar los servidores de símbolos de Microsoft, seleccione **Opciones y configuración** en el menú **Depurar** y, a continuación, elija **Símbolos**. Seleccione **Servidores de símbolos de Microsoft**.  
  
 **Servidores de símbolos de una red interna o del equipo local**  
  
 Su equipo o compañía puede crear servidores de símbolos para sus propios productos y como memoria caché de símbolos de orígenes externos. Podría tener un servidor de símbolos en su propio equipo. Puede especificar la ubicación de los servidores de símbolos como una dirección URL o como una ruta de acceso en la página **Depuración**/**Símbolos** del cuadro de diálogo **Opciones**(¿Por qué Visual Studio requiere que los archivos de símbolos del depurador coincidan exactamente con los archivos binarios con los que se compilaron?).  
  
 **Servidores de símbolos de terceros**  
  
 Los proveedores de aplicaciones Windows y bibliotecas de terceros pueden proporcionar acceso al servidor de símbolos en Internet. También puede escribir la dirección URL de estos servidores de símbolos en la página **Depuración**/**Símbolos** ,  
  
> [!NOTE]
>  Si utiliza un servidor de símbolos distinto de los servidores de símbolos públicos de Microsoft, asegúrese de que el servidor de símbolos y la ruta de acceso son de confianza. Dado que los archivos de símbolos pueden contener código ejecutable arbitrario, puede que se exponga a amenazas de seguridad.  
  
###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Buscar y cargar símbolos durante la depuración  
 En cualquier momento mientras el depurador esté en modo de interrupción, puede cargar símbolos de un módulo que se haya excluido previamente mediante las opciones del depurador o que el compilador no haya podido encontrar. Puede cargar símbolos desde los menús contextuales de las ventanas Pila de llamadas, Módulos, Variables locales, Automático y todas las ventanas Inspección. Si el depurador interrumpe la ejecución en código que no tiene archivos de símbolos o de código fuente disponibles, aparece una ventana de documento. Aquí puede encontrar información sobre los archivos que faltan y tomar medidas para encontrarlos y cargarlos.
  
 **Buscar símbolos con las páginas de documento No se cargaron símbolos**  
  
 El depurador puede interrumpir el código que no tiene símbolos disponibles de varias maneras:  
  
1.  Depurar paso a paso el código.  
  
2.  Interrumpir el código desde un punto de interrupción o una excepción.  
  
3.  Cambiar a un subproceso diferente.  
  
4.  Cambiar el marco de pila haciendo doble clic en un marco de la ventana Pila de llamadas.  
  
 Cuando se produce uno de estos eventos, el depurador muestra la página **No se cargaron símbolos** para ayudar a encontrar y cargar los símbolos necesarios.  
  
 ![No hay ninguna página se cargaron símbolos](../debugger/media/dbg_nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
-   Para cambiar las rutas de acceso de búsqueda, elija una ruta de acceso no seleccionada o elija **Nuevo** y escriba una nueva ruta de acceso. Elija **Cargar** para buscar de nuevo las rutas de acceso y cargar el archivo de símbolos si se encuentra.  
  
-   Elija **examinar y buscar**_nombre-ejecutable_**...**  para invalidar cualquier opción de símbolo y reintentar las rutas de búsqueda. Si se encuentra el archivo de símbolos se carga, o se muestra un Explorador de archivos para que seleccione manualmente el archivo de símbolos.  
  
-   Elija **cambiar la configuración de símbolos...**  para mostrar el **depuración** > **símbolos** página del cuadro de diálogo Opciones de VS.  
  
-   Elija **ver desensamblado** para mostrar el desensamblado en una nueva ventana una vez.  
  
-   Para mostrar siempre el desensamblado cuando no se encuentren los archivos de código fuente o de símbolos, elija el vínculo **Cuadro de diálogo Opciones** y seleccione **Habilitar la depuración de nivel de dirección** y **Mostrar desensamblado si el código fuente no está disponible**.  
  
     ![Opciones de &#47; depuración &#47; opciones generales de desensamblado](../debugger/media/dbg_options_general_disassembly_checkbox.png "DBG_Options_General_disassembly_checkbox")  
  
 **Cambiar opciones de símbolo desde el menú contextual**  
  
 Mientras está en modo de interrupción, puede buscar y cargar los símbolos de los elementos que se muestran en las ventanas Pila de llamadas, Módulos, Variables locales, Automático y en todas las ventanas Inspección. Seleccione un elemento de la ventana, abra el menú contextual y elija una de las opciones siguientes:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Cargar símbolos**|Intenta cargar símbolos desde las ubicaciones especificadas en el **depuración**/**símbolos** página de la **opciones** cuadro de diálogo. Si no se encuentra el archivo de símbolos, se inicia el Explorador de archivos para poder especificar una nueva ubicación en la que buscar.|  
|**Información de carga de símbolos**|Presenta información que muestra la ubicación de un archivo de símbolos cargado, o las ubicaciones buscadas en caso de que el depurador no encuentre el archivo.|  
|**Configuración de símbolos...**|Se abre el **depuración**/**símbolos** página de VS **opciones** cuadro de diálogo.|  
|**Cargar siempre automáticamente**|Agrega el archivo de símbolos a la lista de archivos que el depurador carga automáticamente.|  
  
###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Establecer opciones del compilador para archivos de símbolos  
 Cuando compila un proyecto mediante el IDE de VS y utiliza la configuración de compilación de **depuración** estándar, los compiladores administrados y de C++ crean archivos de símbolos adecuados para el código. También puede establecer opciones del compilador en la línea de comandos para crear los archivos de símbolos.  
  
 **Opciones de C++**  
  
 Un archivo de base de datos de programa (.pdb) contiene información sobre el estado de la depuración y del proyecto que permite la vinculación incremental de una configuración Debug del programa. Cuando se compila con [/ZI o /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) (para C/C++) se crea un archivo .pdb.  
  
 En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], la opción [/Fd](/cpp/build/reference/fd-program-database-file-name) asigna nombre al archivo .pdb creado por el compilador. Al crear un proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante los asistentes, la opción **/Fd** se establece para crear un archivo .pdb denominado *project*.pdb.  
  
 Si compila una aplicación de C/C++ mediante un archivo Make y especifica **/ZI** o **/Zi** sin **/Fd**, terminará con dos archivos .pdb:  
  
-   VC*x*.pdb, donde *x* representa la versión de Visual C++, por ejemplo VC11.pdb. Este archivo almacena toda la información de depuración de los archivos OBJ individuales y reside en el mismo directorio que el archivo MAKE del proyecto.  
  
-   proyecto.pdb   Este archivo almacena toda la información de depuración del archivo .exe. En C/C++, este archivo reside en el subdirectorio \debug.  
  
 Cada vez que crea un archivo OBJ, el compilador de C/C++ combina la información de depuración en VC*x*.pdb. La información insertada incluye información de tipo, pero no información de símbolo como definiciones de función. Por tanto, incluso si cada archivo de código fuente incluye archivos de encabezado comunes como \<windows.h >, las definiciones de tipo de esos encabezados se almacenan en una sola vez, en lugar de aparecer en cada archivo OBJ.  
  
 El vinculador crea el archivo proyecto.pdb, que contiene información de depuración del archivo EXE del proyecto. El archivo proyecto.pdb contiene toda la información de depuración, incluidos los prototipos de función, y no solo la información de tipo que se encuentra en VC*x*.pdb. Ambos archivos .pdb permiten actualizaciones incrementales. El vinculador también incrusta la ruta de acceso al archivo .pdb en el archivo .exe o .dll que crea.  
  
 El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza la ruta de acceso al archivo .pdb en el archivo EXE o DLL para buscar el archivo proyecto.pdb. Si el depurador no puede encontrar el archivo .pdb en dicha ubicación o si la ruta de acceso no es válida (por ejemplo, si el proyecto se ha movido a otro equipo), el depurador busca la ruta que contiene el archivo EXE, las rutas de acceso de símbolos especificadas en el cuadro de diálogo **Opciones** (carpeta**Depuración** , nodo **Símbolos** ). El depurador no cargará un archivo .pdb que no coincida con el archivo ejecutable que se está depurando. Si el depurador no encuentra ningún archivo .pdb, aparecerá el cuadro de diálogo **Buscar símbolos** que permite buscar símbolos o agregar más ubicaciones a la ruta de acceso de búsqueda.  
  
 **Opciones de .NET Framework**  
  
 Un archivo de base de datos de programa (.pdb) contiene información sobre el estado de la depuración y del proyecto que permite la vinculación incremental de una configuración Debug del programa. Cuando se compila con **/debug**, se crea un archivo .pdb. Puede compilar las aplicaciones con **/debug:full** o **/debug:pdbonly**. La compilación mediante **/debug:full** genera código depurable. La compilación mediante **/debug:pdbonly** genera archivos .pdb, pero no genera el atributo `DebuggableAttribute` que indica al compilador JIT que existe información de depuración disponible. Use **/debug:pdbonly** si quiere generar archivos .pdb para una compilación de versión que no quiere que sea depurable. Para obtener más información, vea [/debug (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) o [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).  
  
 El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza la ruta de acceso al archivo .pdb en el archivo EXE o DLL para buscar el archivo proyecto.pdb. Si el depurador no encuentra el archivo .pdb en esa ubicación o si la ruta de acceso no es válida, el depurador busca en la ruta de acceso que contiene el archivo EXE y, a continuación, en las rutas de acceso de símbolos especificadas en el cuadro de diálogo **Opciones** . Esta ruta de acceso generalmente es la carpeta **Depuración** en el nodo **Símbolos** . El depurador no cargará un archivo .pdb que no coincida con el archivo ejecutable que se está depurando. Si el depurador no encuentra ningún archivo .pdb, aparecerá el cuadro de diálogo **Buscar símbolos** que permite buscar símbolos o agregar más ubicaciones a la ruta de acceso de búsqueda.  
  
 **Aplicaciones web**  
  
 El archivo de configuración de la aplicación (Web.config) se debe establecer en modo de depuración. El modo de depuración hace que ASP.NET genere símbolos para los archivos generados dinámicamente y permite al depurador asociarse a la aplicación ASP.NET. Visual Studio lo establece automáticamente cuando empiece a depurar, si ha creado el proyecto de la plantilla de proyectos Web.  
  
##  <a name="BKMK_Find_source_files"></a> Buscar archivos de código fuente  
  
###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Dónde busca el depurador los archivos de código fuente  
 El depurador busca los archivos de código fuente en las siguientes ubicaciones:  
  
1.  Archivos abiertos en el IDE de la instancia de Visual Studio que inició el depurador.  
  
2.  Archivos de la solución abierta en la instancia de Visual Studio.  
  
3.  Los directorios especificados en el **propiedades comunes**/**depurar archivos de código fuente** página en las propiedades de la solución. (En el **Explorador de soluciones**, seleccione el nodo de la solución, haga clic con el botón derecho y seleccione **Propiedades**). )  
  
4.  Información de origen del archivo .pdb del módulo. Puede ser la ubicación del archivo de código fuente cuando se compiló el módulo, o puede ser un comando para un servidor de origen.  
  
###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Buscar y cargar archivos de origen con las páginas No Source/No se cargaron símbolos  
 Cuando el depurador interrumpe la ejecución en una ubicación en la que no está disponible el archivo de código fuente, mostrará las páginas **No se cargaron orígenes** o **No se cargaron símbolos** que pueden ayudarle a buscar el archivo de código fuente. **No se cargaron símbolos** aparece cuando el depurador no encuentra un archivo de símbolos (.pdb) para que el archivo ejecutable complete su búsqueda. La página No se cargaron símbolos proporciona opciones para buscar el archivo. Si se encuentra el archivo .pdb después de ejecutar una de las opciones y el depurador puede recuperar el archivo de origen con la información del archivo de símbolos, se muestra el origen. De lo contrario, aparece una página **No se cargaron orígenes** que describe el problema. La página muestra vínculos de opciones que pueden realizar acciones que podrían resolver el problema.  
  
###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Agregar rutas de acceso de búsqueda de archivo de código fuente a una solución  
 Puede especificar una red o directorios locales para buscar archivos de código fuente.  
  
1.  Seleccione la solución en el Explorador de soluciones y, a continuación, elija **Propiedades** en el menú contextual.  
  
2.  Bajo el nodo **Propiedades comunes** , elija **Depurar archivos de código fuente**.  
  
3.  Haga clic en la carpeta ![herramientas&#47; opciones&#47; depuración&#47;icono de carpeta Symbols](../debugger/media/dbg_tools_options_foldersicon.png "DBG_Tools_Options_FoldersIcon") icono. En la lista **Directorios que contienen código fuente** , aparece texto modificable.  
  
4.  Agregue la ruta de acceso que desee buscar.  
  
 Observe que solo se busca el directorio especificado. Debe agregar entradas para cualquier subdirectorio que desee buscar.  
  
###  <a name="BKMK_Use_source_servers"></a> Usar servidores de origen  
 Cuando no existe código fuente en el equipo local o el archivo .pdb no coincide con el código fuente, puede utilizar el servidor de origen como ayuda para depurar una aplicación. El servidor de origen recoge solicitudes de archivos y devuelve archivos reales. El servidor de origen se ejecuta mediante un archivo DLL denominado srcsrv.dll. El servidor de origen lee el archivo .pdb de la aplicación, que contiene punteros al repositorio de código fuente, y comandos que se utilizan para recuperar el código fuente del repositorio. Puede restringir qué comandos se pueden ejecutar a partir del archivo .pdb de la aplicación especificando la lista de comandos permitidos dentro de un archivo denominado srcsrv.ini, que debe encontrarse en el mismo directorio que srcsrv.dll y devenv.exe.  
  
> [!IMPORTANT]
>  En el archivo .pdb de la aplicación se pueden incrustar comandos arbitrarios, por lo que debe asegurarse de colocar únicamente los que desee ejecutar en el archivo srcsrv.ini. Todo intento de ejecutar un comando no incluido en el archivo srcsvr.ini provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, consulta [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). No se realiza ninguna validación de los parámetros de comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si confiara en cmd.exe, un usuario malintencionado podría especificar parámetros que harían que el comando fuera peligroso.  
  
 **Para habilitar el uso de un servidor de origen**  
  
1.  Asegúrese de cumplir las medidas de seguridad descritas en la sección anterior.  
  
2.  En el menú **Herramientas** , elija **Opciones**.  
  
     Aparecerá el cuadro de diálogo **Opciones** .  
  
3.  En el nodo **Depuración** , elija **General**.  
  
4.  Active la casilla **Habilitar compatibilidad de servidor de origen** .  
  
     ![Habilitar las opciones de servidor de origen](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  
  
5.  (Opcional) Elija las opciones secundarias que desee.  
  
     Observe que tanto **Permitir servidor de origen para ensamblados de confianza parcial (solo administrado)** como **Ejecutar siempre los comandos del servidor de origen que no sean de confianza sin preguntar** pueden aumentar los riesgos para la seguridad descritos anteriormente.  
  
## <a name="see-also"></a>Vea también  
[Descripción de los archivos de símbolos y la configuración de símbolos de Visual Studio](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)

[Carga los cambios en Visual Studio 2012 y 2013 remota de símbolos de .NET](https://blogs.msdn.microsoft.com/devops/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
