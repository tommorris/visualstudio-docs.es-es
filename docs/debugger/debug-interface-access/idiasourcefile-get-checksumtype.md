---
title: 'Idiasourcefile:: Get_checksumtype | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83d1aa687ec7f19df61031d4ff334751ccabaebd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461936"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Recupera el tipo de suma de comprobación.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el tipo de suma de comprobación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El tipo de suma de comprobación es un valor que se pueden asignar a un algoritmo de suma de comprobación. Por ejemplo, el formato de archivo PDB estándar normalmente puede tener uno de los siguientes valores:  
  
|Tipo de suma de comprobación|Etiqueta de CryptoAPI|Descripción|  
|-------------------|---------------------|-----------------|  
|0|\<Ninguno >|No hay suma de comprobación presente.|  
|1|`CALG_MD5`|la suma de comprobación se genera con el algoritmo hash MD5.|  
|2|`CALG_SHA1`|la suma de comprobación se genera con el algoritmo hash SHA1.|  
  
 El `CryptoAPI` las etiquetas son desde el `ALG_ID` enumeración. Para obtener más información sobre algoritmos hash, consulte el `CryptoAPI` sección de Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Para obtener los bytes de la suma de comprobación real del archivo de origen, llame a la [idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)