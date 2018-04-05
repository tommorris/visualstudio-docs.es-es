---
title: Administrar resultados de pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: f5b09a2350efadafaacdc5fcd530b3c3f50c7419
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga

Cuando se ejecutan pruebas de carga, cualquier información recopilada durante la ejecución de una prueba puede almacenarse en el *repositorio de resultados de pruebas de carga*, que es una base de datos SQL. El repositorio de resultados de pruebas de carga contiene datos de los contadores de rendimiento y cualquier información de errores que se obtenga. La base de datos del repositorio de resultados la crea el programa de instalación para los controladores, o bien se crea automáticamente en la primera ejecución local de una prueba de carga. Para una ejecución local, la base de datos se creará automáticamente si el esquema de la prueba de carga no está presente.

 Si modifica la cadena de conexión del repositorio de resultados del controlador para que se utilice otro servidor, se deberá ejecutar en el nuevo servidor el script loadtestresultsrepository.sql para crear el esquema.

 Visual Studio Enterprise proporciona conjuntos de contadores con nombre que recopilan contadores de rendimiento comunes basados en una tecnología. Estos conjuntos son útiles cuando se está analizando un servidor IIS, un servidor ASP.NET o un servidor SQL. Todos los datos recolectados mediante los conjuntos de contadores se almacenan en el repositorio de resultados de pruebas de carga.

> [!IMPORTANT]
> Existe una diferencia entre un conjunto de contadores y los datos de contadores de rendimiento. Un conjunto de contadores consiste en metadatos. Define un grupo de contadores de rendimiento que deben recolectarse de un equipo que desempeña un rol particular, como un servidor IIS o SQL Server. El conjunto de contadores forma parte de la definición de la prueba de carga. Los datos de contadores de rendimiento se recogen basándose en los conjuntos de contadores, la asignación del conjunto de contadores a un equipo concreto y la velocidad de muestreo.

## <a name="sql-server-versions"></a>Versiones de SQL Server

 Para usar pruebas de carga, puede emplear LocalDB de SQL Server Express, que se instala con Visual Studio. Es el servidor de base de datos predeterminado para las pruebas de carga (incluida la integración de Microsoft Excel). SQL Server Express LocalDB es un modo de ejecución de SQL Server Express destinado a desarrolladores de programas. La instalación de SQL Server Express LocalDB copia un conjunto mínimo de archivos necesario para iniciar el motor de base de datos de SQL Server.

 Si el equipo prevé necesidades de base de datos intensivas, o si los proyectos superan la capacidad de LocalDB de SQL Server Express, debería considerar la actualización a SQL Express o a la versión completa de SQL Server a fin de proporcionar potencial de escalado adicional. Si actualiza SQL Server, los archivos MDF y LDF para LocalDB de SQL Server Express se almacenan en la carpeta de perfil de usuario. Estos archivos se pueden usar para importar la base de datos de pruebas de carga a SQL Server Express o SQL Server.

## <a name="load-test-results-store-considerations"></a>Consideraciones sobre el almacén de resultados de pruebas de carga

 Cuando se instala Visual Studio Enterprise, el almacén de resultados de pruebas de carga se configura para usar una instancia de SQL Express que se instala en el equipo. SQL Express se limita a utilizar un máximo de 4 GB de espacio en disco. Si va a ejecutar muchas pruebas de carga en un período largo de tiempo, debe considerar configurar el almacén de resultados de pruebas de carga para utilizar una instancia completa de SQL Server si está disponible.

## <a name="load-test-analyzer-tasks"></a>Tareas del Analizador de prueba de carga

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Configurar un repositorio de resultados de pruebas de carga:** puede configurar un repositorio de resultados de pruebas de carga en una base de datos SQL. **Nota:** También se puede crear un repositorio de pruebas de carga al instalar un controlador de pruebas. Para obtener más información, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).||
|**Seleccionar y ver un repositorio de resultados:** puede seleccionar un repositorio de resultados concreto. el usuario no está limitado a un almacén de resultados local. Con frecuencia, las pruebas de carga se ejecutan en un conjunto remoto de equipos agente. Los resultados de prueba de los agentes o un equipo local se pueden guardar en cualquier servidor SQL en el que se haya creado un almacén de resultados de pruebas de carga. En cualquier caso, debe identificar dónde almacenar los resultados de pruebas de carga mediante la ventana **Administrar controladores de pruebas**.|-   [Cómo: Seleccionar un repositorio de resultados de pruebas de carga](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md)|
|**Eliminar el resultado de una prueba de carga del repositorio:** puede quitar el resultado de una prueba de carga del **Editor de pruebas de carga** mediante el cuadro de diálogo **Abrir y administrar resultados de pruebas de carga**.|-   [Cómo: Eliminar los resultados de pruebas de carga de un repositorio](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Importar y exportar los resultados en un repositorio:** puede importar y exportar resultados de pruebas de carga en el **Editor de pruebas de carga**.|-   [Cómo: Importar los resultados de pruebas de carga a un repositorio](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Cómo: Exportar los resultados de pruebas de carga de un repositorio](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Tareas relacionadas

 [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

 Puede ver los resultados de una prueba de carga en ejecución y una prueba de carga completada utilizando el Analizador de prueba de carga.

## <a name="see-also"></a>Vea también

- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md)