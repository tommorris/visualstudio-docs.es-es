---
title: 'Idiaaddressmap:: Set_imageheaders | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51b68475b9ef0374f95febabc2997524bfd61259
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458484"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Conjuntos de encabezados para habilitar la traducción de dirección virtual relativa de la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 cbData  
 [in] Número de bytes de datos de encabezado. Debe ser `n*sizeof(IMAGE_SECTION_HEADER)` donde `n` es el número de encabezados de la sección del archivo ejecutable.  
  
 datos]  
 [in] Una matriz de `IMAGE_SECTION_HEADER` estructuras que se usará como los encabezados de la imagen.  
  
 originalHeaders  
 [in] Establecido en `FALSE` si los encabezados de la imagen se corresponden con la nueva imagen, `TRUE` si reflejan la imagen original antes de realizar una actualización. Normalmente, esto se establecería en `TRUE` sólo en combinación con llamadas a la [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El `IMAGE_SECTION_HEADER` estructura se declara en Winnt.h y representa el formato de encabezado de sección de imagen del archivo ejecutable.  
  
 Cálculos de dirección virtual relativa dependen el `IMAGE_SECTION_HEADER` valores. Normalmente, el DIA recupera desde el archivo de programa (.pdb) de la base de datos. Si faltan estos valores, el DIA es no se puede calcular direcciones virtuales relativas y el [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) método `FALSE`. El cliente, a continuación, debe llamar a la [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) método para permitir a los cálculos de dirección virtual relativa después de proporcionar los encabezados que faltan de la imagen de la propia imagen.  
  
## <a name="see-also"></a>Vea también  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)