---
title: JavaScript
description: Información sobre la compatibilidad con Javascript en Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 21ff2211632cba63dafe2a7abf1964e7a89e87c3
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224235"
---
# <a name="javascript-support"></a>Compatibilidad con JavaScript

Visual Studio para Mac proporciona compatibilidad con Javascript y Typescript mediante el resaltado de sintaxis, el formato de código e IntelliSense. 

![compatibilidad del editor de TypeScript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Para obtener más información sobre la escritura de JavaScript, consulte las guías [Escribir código JavaScript](https://docs.microsoft.com/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Agregar un archivo JavaScript

Los archivos JavaScript se suelen agregar a los proyectos de ASP.NET Core mediante el cuadro de diálogo **Nuevo archivo**. Para agregar un archivo JavaScript, haga doble clic en el proyecto y vaya a **Agregar > Nuevo archivo**: 

![agregar archivos nuevos al proyecto](media/javascript-image1.png)

En el cuadro de diálogo Nuevo archivo, seleccione **Web > Archivo JS vacío** o **Web > Archivo Typescript**. Asígnele un nombre y elija **Aceptar**:

![crear un nuevo archivo TypeScript desde la plantilla](media/javascript-image2.png)

## <a name="intellisense"></a>Intellisense

Visual Studio para Mac usa la [Javascript Language Service](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense) para proporcionar IntelliSense, lo que le permite obtener una finalización de código inteligente, información de parámetros y listas de miembros cuando escribe código.

Javascript IntelliSense en Visual Studio para Mac puede basarse en la inferencia de tipos, JSDoc o declaración de Typescript.

- **Inferencia de tipos**: el tipo de un objeto se determina por el contexto del código que lo rodea. Para obtener más información, vea la sección de Visual Studio [IntelliSense basado en la inferencia de tipos](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc**: hay ocasiones en que la inferencia de tipos no proporciona la información de tipo correcta. En estos casos, la información de tipo puede proporcionarse explícitamente por anotaciones [JSDoc](http://usejsdoc.org/about-getting-started.html). Para obtener más información, vea la sección de Visual Studio [IntelliSense basado en JSDoc](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Archivos de declaración de TypeScript**: `.d.ts` los archivos se usan para proporcionar los valores para Javascript Intellisense. Los tipos declarados en ese archivo se pueden usar como tipos en los comentarios de JSDoc. Para obtener más información, vea la sección de Visual Studio [IntelliSense basado en archivos de declaración de TypeScript](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)![agregar un archivo de definición de TypeScript](media/javascript-image3.png)