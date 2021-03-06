---
title: Identidades de los suscriptores de Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Cómo agregar una identidad alternativa a la suscripción de Visual Studio para usar VSTS y Azure
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 30aa1e918e289a6cfe8f11329d5df7682cd90239
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2018
ms.locfileid: "43289371"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identidades de los suscriptores de Visual Studio

Cuando activa una suscripción de Visual Studio, vinculamos la identidad (o inicio de sesión) que ha usado durante la activación con la suscripción de Visual Studio. De esta manera, se le puede reconocer en el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), en Visual Studio Team Services (VSTS) y en Azure.

En VSTS, comprobamos el estado de la suscripción de Visual Studio cada vez que inicia sesión y le concederemos características automáticamente dentro del ámbito de cada cuenta de la que sea miembro.
Dado que estas características se incluyen como una ventaja de suscriptor, no supone un gasto extra incluirle como miembro de una cuenta de VSTS si usa una identidad que está vinculada a su suscripción de Visual Studio.

En Azure, comprobamos el estado de la suscripción de Visual Studio cuando se activa su [crédito mensual de Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), que es una ventaja de suscriptor.

En el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), puede agregar una **identidad alternativa**, además de la identidad que ha usado durante la activación. Actualmente, se permite agregar una identidad alternativa si se ha usado una cuenta Microsoft para activar la suscripción. De este modo, puede agregar también una cuenta profesional o educativa (que use para iniciar sesión en Visual Studio, en Office 365 o en la red de la empresa o del centro educativo), lo que le permitirá tener acceso a VSTS tanto a través de su cuenta personal como de su cuenta profesional o educativa.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Agregar una cuenta alternativa a la suscripción de Visual Studio

La adición de una cuenta alternativa a la suscripción de Visual Studio permite acceder a las ventajas de la suscripción, como Visual Studio Team Services (VSTS) y Azure, con una identidad diferente a la que se asigna la suscripción. En el pasado, esta funcionalidad solo estaba disponible si la suscripción de Visual Studio (VS) se había asignado a una cuenta Microsoft (MSA). Se ha ampliado esta funcionalidad para cuentas profesionales o educativas de Azure Active Directory (Azure AD).

No proporciona una copia de suscripción a la otra cuenta; simplemente ofrece la posibilidad de acceder a las dos ventajas con la cuenta alternativa.

En todas las suscripciones puede agregar una "cuenta profesional o educativa" para usarla con las ventajas que requieren un inicio de sesión (IDE de VS, VSTS y Azure).


### <a name="add-the-alternate-account"></a>Agregar la cuenta alternativa


1. Inicie sesión en el portal de suscriptores de Visual Studio con la cuenta de Microsoft (https://my.visualstudio.com).

2. Vaya a **Suscripciones**.

    > [!div class="mx-imgBorder"]
    > ![Agregar una cuenta alternativa: Ir a suscripciones en VS](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Elija **Agregar cuenta alternativa**.
    > [!div class="mx-imgBorder"]
    > ![Elegir Agregar cuenta alternativa](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Agregue la cuenta profesional o educativa.
    > [!div class="mx-imgBorder"]
    > ![Agregar cuenta profesional o educativa](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Use su cuenta profesional o educativa para iniciar sesión en Visual Studio Team Services (https://{suCuenta}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Usar la cuenta profesional o educativa](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

La cuenta alternativa se agrega a la suscripción de Visual Studio, lo que permite que ambas identidades usen las ventajas de la suscripción que requieren que inicie sesión con la cuenta alternativa (IDE, VSTS y Azure).

## <a name="faq"></a>Preguntas más frecuentes

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>P: ¿Por qué VSTS no me reconoce como suscriptor de Visual Studio?

R: VSTS debería reconocer la suscripción automáticamente cuando inicie sesión con su identidad principal o alternativa. Si no es así, puede probar a hacer lo siguiente:

* Compruebe que tiene una suscripción de Visual Studio activa que [incluye VSTS como ventaja](vs-vsts.md).

* Confirme que está usando un inicio de sesión/identidad que es la identidad principal o alternativa de su suscripción de Visual Studio.

* Vaya al [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) al menos una vez antes de iniciar sesión en VSTS.

Si VSTS sigue sin reconocer la suscripción, [póngase en contacto con el equipo de soporte técnico](https://visualstudio.microsoft.com/team-services/support/).
