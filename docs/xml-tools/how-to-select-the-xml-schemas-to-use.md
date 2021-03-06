---
title: 'Cómo: Seleccionar los esquemas XML que se van a usar'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d835a8592108b549a109f7bb7e128a8ae5b01611
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549108"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Cómo: seleccionar los esquemas XML para usar

El Editor XML proporciona una caché de esquema que está ubicada en el *%InstallDir%\Xml\Schemas* directory. La caché de esquema incluye esquemas XML muy conocidos que se utilizan en IntelliSense y en la validación de documentos XML.

El **esquemas** propiedad de documento se utiliza para seleccionar uno o más XML esquema definición XSD (lenguaje) que se van a usar. Permite seleccionar esquemas de la caché de esquema o especificar un esquema que no está ubicado en la caché.

Los esquemas especificados se guardan en el archivo oculto de opciones de usuario de solución (. *suo*), junto con todo el código XML otra propiedades del documento. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

> [!NOTE]
> El editor puede realizar la validación mediante un esquema alineado o un esquema al que se haga referencia en el atributo `xsd:schemaLocation`. Para obtener más información, consulte [validación de documentos XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para seleccionar un esquema XML de la caché de esquema

1.  Abra un archivo en el Editor XML.

2.  En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.

     El **esquemas XML** se muestra el cuadro de diálogo. El cuadro de diálogo enumera todos los esquemas con una. *xsd* extensión en la caché de esquema (incluidos los esquemas que se hace referencia en el *catalog.xml* archivo) y también cualquier esquema que está en la solución actual, abierta en Visual Studio, al que hace referencia en un `xsd:schemaLocation` atributo o se hace referencia en el **esquemas** propiedad.

3.  Seleccione los esquemas que desea utilizar en la validación mediante una de las siguientes acciones:

    -   Seleccione un esquema que aparece en el **esquemas XML** cuadro de diálogo, haga clic en el **Use** columna y, a continuación, seleccione **utilizar este esquema**.

     -o bien-

    -   Seleccione varios esquemas que aparecen en la **esquemas XML** cuadro de diálogo, menú contextual y seleccione **utilizar este esquema**.

4.  Haga clic en **Aceptar**.

     La lista de esquemas seleccionados se copia en el **esquemas** propiedad del documento.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para agregar un esquema XML a la caché de esquema

1.  En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.

2.  Haga clic en **Agregar**.

     Se abrirá la **Abrir esquema XSD** cuadro de diálogo.

3.  Busque y seleccione los esquemas que se van a agregar a la caché de esquema.

4.  Haga clic en **abiertos**.

     El esquema se agrega al esquema de caché y es el **Use** valor de la columna se establece en **utilizar este esquema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para eliminar un esquema XML de la caché de esquema

1.  En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.

2.  Seleccione el esquema que desea quitar y, a continuación, haga clic en **quitar**.

     El esquema se quita de la caché de esquema en memoria, pero no del sistema de archivos.

    > [!NOTE]
    > Si todavía existe una referencia al esquema a través de un `schemaLocation` atributo o una coincidencia con `targetNamespace` , a continuación, **quitar** no funcionará en esta situación debido a una asociación automática. En este caso, se recomienda que marque el esquema como **no utilizar esquemas seleccionados** en el **usar** columna.

## <a name="see-also"></a>Vea también

- [Caché de esquema](../xml-tools/schema-cache.md)
- [Cuadro de diálogo de esquemas XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)