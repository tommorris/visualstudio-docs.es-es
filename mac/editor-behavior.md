---
title: Comportamiento del editor
description: En este artículo se describen las distintas opciones que pueden usarse para modificar el comportamiento del editor de texto en Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 4d40d03bde0323ce44b9de6ff1ae13e281f0ed6c
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "43223927"
---
# <a name="editor-behavior"></a>Comportamiento del editor

Puede establecer los comportamientos del editor de modo que permitan aplicar formato al código mientras se escribe. Estas acciones se establecen en **Visual Studio > Preferencias… > Editor de texto > Comportamiento**. Más abajo se describen algunas de las funciones más usadas:

![Opciones de comportamiento del editor](media/source-editor-image9.png)

*  Se pueden agregar llaves de cierre automáticamente al código al crear clases, métodos o propiedades. Cuando se selecciona esta opción, al escribir `{` se agregará `}` automáticamente.
* La aplicación de formato de código sobre la marcha se activa al pulsar caracteres (por ejemplo, el punto y coma o las llaves), lo que emulará las preferencias de formato establecidas.
* También puede optar por aplicar formato al archivo al guardarlo, lo que permite escribir el código libremente y hace que el IDE sea el responsable de aplicarle formato según las preferencias existentes.
* La sangría se puede establecer en Ninguna, Automática o Inteligente. Hacen lo siguiente:
 * Ninguna: establece el símbolo de inserción al principio de la línea siguiente.
 * Automática: establece el símbolo de inserción en la misma columna de la línea siguiente.
 * Inteligente: aplica la sangría en la línea siguiente en función del código.
* El comportamiento de separación de palabras difiere entre los sistemas operativos y, con vistas a la navegación, el editor de texto debe saber dónde empiezan y acaban las palabras. El formato se puede establecer en Unix o Windows.

También puede establecer reglas de formato para XML, CSS, HTML y JSON.