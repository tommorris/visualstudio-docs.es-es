---
title: Herramientas XML en Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 446378df2d73f4d0c2bb8eac45075fa51365cd6d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693739"
---
# <a name="xml-tools-in-visual-studio"></a>Herramientas XML en Visual Studio

*Lenguaje de marcado extensible (XML)* es un lenguaje de marcado que proporciona un formato para describir datos. Esto facilita declaraciones más precisas del contenido y resultados de búsqueda más útiles en varias plataformas. Además, XML permite separar la presentación de los datos. Por ejemplo, en HTML se usan etiquetas para indicar al explorador que muestre los datos en negrita o cursiva, pero en XML las etiquetas solo se usan para describir los datos, como el nombre de la ciudad, la temperatura y la presión atmosférica. En XML, se usan las hojas de estilos como Extensible Stylesheet Language (XSL) y hojas de estilos en cascada (CSS) para presentar los datos en un explorador. XML separa los datos de la presentación y el proceso. Esto le permite mostrar y procesar los datos como desee por medio de distintas hojas de estilo y aplicaciones.

XML es un subconjunto de SGML optimizado para entregarse a través de Internet. Lo define World Wide Web Consortium (W3C). Esta estandarización garantiza que los datos estructurados sean uniformes e independientes de las aplicaciones o los proveedores.

XML es el núcleo de muchas características de Visual Studio y .NET Framework. La siguiente lista de artículos mencionan las herramientas y características relacionadas con XML que se ofrecen en Visual Studio y .NET Framework.

Para obtener más información, consulte el <xref:System.Xml?displayProperty=fullName> documentación.

## <a name="reference"></a>Referencia

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) expone la [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) árbol a través de análisis [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) para cualquier documento XML.

[Referencia de los estándares XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) proporciona información acerca de las tecnologías XML, como XML, definición de tipo de documento (DTD), lenguaje de definición de esquemas XML (XSD) y XSLT.

<xref:System.Xml?displayProperty=fullName> Describe las clases y otros elementos que componen el <xref:System.Xml> espacio de nombres y proporciona vínculos a información más detallada sobre cada elemento.

<xref:System.Xml.Serialization?displayProperty=fullName> Describe las clases y otros elementos que componen el <xref:System.Xml.Serialization> espacio de nombres y se proporcionan vínculos a información más detallada acerca de cada elemento.

## <a name="related-sections"></a>Secciones relacionadas

[Modelo de objetos de documento (DOM) XML](/dotnet/standard/data/xml/xml-document-object-model-dom) describe cómo la <xref:System.Xml.XmlDocument> y sus clases asociadas cumplen con las especificaciones de compatibilidad de espacio de nombres de nivel 2 y W3C Document Object Model (Core) nivel 1.

[Procesar datos XML con XmlWriter y XmlReader](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[Las transformaciones XSLT](/dotnet/standard/data/xml/xslt-transformations) describe cómo la <xref:System.Xml.Xsl.XslCompiledTransform> clase implementa la recomendación de XSLT 1.0.

[Procesar datos XML utilizando el modelo de datos XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) describe cómo la <xref:System.Xml.XPath.XPathNavigator> clase puede procesar datos XML almacenados en una <xref:System.Xml.XPath.XPathDocument> o un <xref:System.Xml.XmlDocument> objeto. La clase <xref:System.Xml.XPath.XPathNavigator> se basa en el modelo de datos de XQuery 1.0 y XPath 2.0 y se puede usar para navegar por los datos XML y editarlos.

[Modelo de objetos de esquema XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som) describe las clases utilizadas para crear y manipular esquemas XML, proporcionando un <xref:System.Xml.Schema.XmlSchema> clase para cargar y editar un esquema.