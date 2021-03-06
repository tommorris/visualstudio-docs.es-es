---
title: Función SccWillCreateSccFile | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6da09badf0ffea4846d35fe00b4ca146243d64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137059"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (función)
Esta función determina si el complemento de control de origen admite la creación de la MSSCCPRJ. Archivo de control de código fuente para cada uno de los archivos determinados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 nFiles  
 [in] El número de nombres de archivo que se incluye en el `lpFileNames` de matriz, así como la longitud de la `pbSccFiles` matriz.  
  
 lpFileNames  
 [in] Una matriz de nombres de archivo completo para comprobar (la matriz debe asignarse al llamador).  
  
 pbSccFiles  
 [entrada, salida] Matriz en la que se va a almacenar los resultados.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_E_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|  
|SCC_E_NONSPECIFICERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se invoca con una lista de archivos para determinar si el complemento de control de código fuente proporciona compatibilidad en el MSSCCPRJ. Archivo de control de código fuente para cada uno de los archivos determinados (para obtener más información sobre la MSSCCPRJ. Archivo de control de código fuente, consulte [MSSCCPRJ. Archivo de control de código fuente](../extensibility/mssccprj-scc-file.md)). Los complementos de control de código fuente pueden declarar si tienen la capacidad de crear MSSCCPRJ. Archivos de control de código fuente mediante la declaración de `SCC_CAP_SCCFILE` durante la inicialización. El complemento devuelve `TRUE` o `FALSE` por cada archivo en el `pbSccFiles` matriz para indicar cuál de los archivos determinados tiene MSSCCPRJ. Compatibilidad con el control de código fuente. Si el complemento devuelve un código correcto de la función, se respetan los valores de la matriz de devolución. En caso de error, se omite la matriz.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)