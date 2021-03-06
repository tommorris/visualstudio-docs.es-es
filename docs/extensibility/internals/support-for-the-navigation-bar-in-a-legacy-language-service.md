---
title: Compatibilidad con la barra de navegación en un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d4dd17f3bb1bd50a97b24b42cf40edc27bf51db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134666"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Compatibilidad con la barra de navegación en un servicio de lenguaje heredado
La barra de navegación en la parte superior de la vista del editor muestra los tipos y miembros en el archivo. Los tipos se muestran en la lista desplegable izquierda y los miembros se muestran en el derecho de la lista desplegable. Cuando el usuario selecciona un tipo, el símbolo de intercalación se coloca en la primera línea del tipo. Cuando el usuario selecciona un miembro, el símbolo de intercalación se coloca en la definición del miembro. Los cuadros de lista desplegable se actualizan para reflejar la ubicación actual del símbolo de intercalación.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Mostrar y actualizar la barra de navegación  
 Para admitir la barra de navegación, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> clase e implemente el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método. Cuando el servicio de lenguaje tiene una ventana de código, la base de <xref:Microsoft.VisualStudio.Package.LanguageService> crea una instancia de la clase la <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, que contiene el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto que representa la ventana de código. El <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , a continuación, se proporciona al objeto un nuevo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto. El <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método obtiene un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto. Si devolver una instancia de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (clase), el <xref:Microsoft.VisualStudio.Package.CodeWindowManager> llamadas su <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método para rellenar el texto interno se enumeran y pasa su <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> el objeto a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desplegable barra manager. La lista desplegable barra manager, a su vez, llama a la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> método en su <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto que se va a establecer el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> objeto que contiene las dos barras de la lista desplegable.  
  
 Cuando se mueve el símbolo de intercalación, el <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> método. La base de <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método en su <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> clase para actualizar el estado de la barra de navegación. Pasar un conjunto de <xref:Microsoft.VisualStudio.Package.DropDownMember> objetos a este método. Cada objeto representa una entrada en la lista desplegable.  
  
## <a name="the-contents-of-the-navigation-bar"></a>El contenido de la barra de navegación  
 La barra de navegación normalmente contiene una lista de tipos y una lista de miembros. La lista de tipos incluye todos los tipos disponibles en el archivo de origen actual. Los nombres de tipo incluyen la información de espacio de nombres completo. El siguiente es un ejemplo de código C# con dos tipos:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Se mostrará la lista de tipos `TestLanguagePackage.TestLanguageService` y `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 La lista de miembros muestra a los miembros disponibles del tipo seleccionado en la lista de tipos. En el ejemplo de código anterior, si `TestLanguagePackage.TestLanguageService` es el tipo que está seleccionado, la lista de miembros contendría los miembros privados `tokens` y `serviceName`. La estructura interna `Token` no se muestra.  
  
 Puede implementar la lista de miembros para que el nombre de un miembro esté en negrita cuando el símbolo de intercalación se coloca dentro de él. Los miembros también puede mostrarse en gris texto, que indica que no están dentro del ámbito donde se encuentra situado actualmente el símbolo de intercalación.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Habilitar la compatibilidad de la barra de navegación  
 Para habilitar la compatibilidad de la barra de navegación, debe establecer el `ShowDropdownBarOption` parámetro de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribuir a `true`. Este parámetro establece la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Para admitir la barra de navegación, debe implementar la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto en el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.  
  
 En la implementación de la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método, si la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> propiedad está establecida en `true`, puede devolver un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto. Si no se devuelven el objeto, no se muestra la barra de navegación.  
  
 Puede establecerse la opción para mostrar la barra de navegación por el usuario, por lo que es posible que este control se restablezca mientras la vista del editor está abierta. El usuario debe cerrar y volver a abrir la ventana del editor para que el cambio realiza.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementar la compatibilidad de la barra de navegación  
 El <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método toma dos listas (uno para cada lista desplegable) y dos valores que representa la selección actual en cada lista. Las listas y los valores de selección se pueden actualizar, en cuyo caso el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método debe devolver `true` para indicar que se han cambiado las listas.  
  
 A medida que cambia la selección en la lista desplegable de tipos, la lista de miembros debe actualizarse para reflejar el nuevo tipo. Lo que se muestra en la lista de miembros puede ser:  
  
-   La lista de miembros para el tipo actual.  
  
-   Todos los miembros disponibles en el origen de archivo, pero con todos los miembros no está en el tipo actual se muestran en texto atenuado. El usuario todavía puede seleccionar a los miembros deshabilitado, por lo que pueden utilizarse para una navegación rápida, pero el color indica que no forman parte del tipo actualmente seleccionado.  
  
 Una implementación de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método suele llevar a cabo los pasos siguientes:  
  
1.  Obtener una lista de declaraciones actuales del archivo de origen.  
  
     Hay varias maneras para rellenar las listas. Un enfoque consiste en crear un método personalizado de la versión de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase que llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método con un motivo de análisis personalizado que devuelve una lista de todas las declaraciones. Otro enfoque podría ser llamar a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método directamente desde el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método con la razón de análisis personalizada. Un tercer enfoque podría ser para almacenar en caché las declaraciones en el <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase devuelta por la última operación de análisis completa en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase y recuperar de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método.  
  
2.  Rellenar o actualizar la lista de tipos.  
  
     El contenido de la lista de tipos puede actualizarse cuando el origen ha cambiado o si ha elegido cambiar el estilo del texto de los tipos basados en la posición del símbolo de intercalación actual. Tenga en cuenta que esta posición se pasa a la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método.  
  
3.  Determinar el tipo para seleccionarlo en la lista de tipos basándose en la posición actual del símbolo de intercalación.  
  
     Puede buscar las declaraciones que se obtuvieron en el paso 1 para buscar el tipo que rodea la posición actual del símbolo de intercalación y, a continuación, busque en la lista de tipos para ese tipo determinar su índice en la lista de tipos.  
  
4.  Rellenar o actualizar la lista de miembros en función del tipo seleccionado.  
  
     La lista de miembros refleja lo que se muestra actualmente en el **miembros** lista desplegable. El contenido de la lista de miembros que necesite actualizarse si el origen ha cambiado o si se muestran a solo los miembros del tipo seleccionado y ha cambiado el tipo seleccionado. Si decide mostrar a todos los miembros en el archivo de origen, a continuación, el estilo del texto de cada miembro en la lista debe actualizarse si ha cambiado el tipo seleccionado actualmente.  
  
5.  Determinar el miembro que se va a seleccionar en la lista de miembros en función de la posición del símbolo de intercalación actual.  
  
     Buscar las declaraciones que se obtuvieron en el paso 1 para el miembro que contiene la posición actual del símbolo de intercalación, a continuación, busque en la lista de miembros de ese miembro determinar su índice en la lista de miembros.  
  
6.  Devolver `true` si los cambios se realizaron en las listas o la selección de cualquiera de las listas.