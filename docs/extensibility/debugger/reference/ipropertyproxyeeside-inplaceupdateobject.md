---
title: IPropertyProxyEESide::InPlaceUpdateObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf62b75fb421cdfb6ad323fbdd12958f93991254
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31124912"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Actualiza los datos del objeto con el objeto de datos especificada y devuelve un nuevo objeto de datos que representa los datos del objeto nuevo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dataIn`  
 [in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contiene los nuevos datos.  
  
 `dataOut`  
 [out] Devuelve un nuevo `IEEDataStorage` objeto que contiene los datos reemplazados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método realmente actualiza los datos del objeto. Los datos en el valor devuelto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto no necesita ser el mismo que los datos de entrada `IEEDataStorage` objeto, pero el objeto devuelto debe reflejar el valor actual de la propiedad.  
  
 El objeto de datos entrante no se suele implementar en lo EE. Sin embargo, el objeto devuelto por este método siempre se implementa mediante lo EE, lo que permite el implementan EE el `IEEDataStorage` interfaz en cualquier clase que se desea.  
  
 El [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) método crea un objeto de datos basado en el objeto de datos entrantes pero no afecta a los datos originales de la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)