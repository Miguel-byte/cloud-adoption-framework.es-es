---
title: Centralización de operaciones de administración
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Instrucciones para centralizar las operaciones de administración
author: JnHs
ms.author: jenhayes
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: b88a1541a2f96dbd4b8d63572e44d493bce8cc45
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72979957"
---
# <a name="centralize-management-operations"></a>Centralización de operaciones de administración

Para la mayoría de las organizaciones, el uso de un único inquilino de Azure Active Directory (Azure AD) para todos los usuarios simplifica las operaciones de administración y reduce los costos de mantenimiento. Esto se debe a que todas las tareas de administración pueden realizarlas usuarios designados, grupos de usuarios o entidades de servicio dentro de ese inquilino. 

Si es posible, se recomienda que use un único inquilino de Azure AD en cada organización. No obstante, algunas situaciones pueden requerir que una organización mantenga varios inquilinos de Azure AD por los siguientes motivos:

- Es una subsidiaria totalmente independiente.
- Funciona de forma independiente en varias zonas geográficas.
- Se aplican determinados requisitos de cumplimiento o de tipo legal.
- Se adquirieron otras organizaciones (a veces de forma temporal hasta que se define una estrategia de consolidación de inquilinos a largo plazo).

Cuando se requiere una arquitectura de multiinquilino, [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/overview) proporciona una manera de centralizar y simplificar las operaciones de administración. Las suscripciones de varios inquilinos se pueden incorporar para la [administración de recursos delegados de Azure](https://docs.microsoft.com/azure/lighthouse/concepts/azure-delegated-resource-management). Esta opción permite a los usuarios especificados en el inquilino de administración realizar [funciones de administración entre inquilinos](https://docs.microsoft.com/azure/lighthouse/concepts/cross-tenant-management-experience) de una manera centralizada y escalable.

Por ejemplo, supongamos que su organización tiene un solo inquilino, *Inquilino A*. Posteriormente, la organización adquiere dos inquilinos adicionales, *Inquilino B* e *Inquilino C* y, por motivos empresariales, ambos deben mantenerse como inquilinos independientes.

Su organización quiere usar las mismas definiciones de directiva, prácticas de copia de seguridad y procesos de seguridad en todos los inquilinos. Dado que ya tiene usuarios (incluidos los grupos de usuarios y las entidades de servicio) que son responsables de realizar estas tareas en el Inquilino A, puede incorporar todas las suscripciones en el Inquilino B y el Inquilino C, con el fin de que los mismos usuarios del Inquilino A puedan realizar esas mismas tareas. El inquilino A se convierte en el inquilino de administración para el inquilino B y el inquilino C.

![Los usuarios del Inquilino A administran los recursos del Inquilino B y del Inquilino C](../_images/manage/enterprise-azure-lighthouse.jpg)

Para más información, consulte [Azure Lighthouse en escenarios empresariales](https://docs.microsoft.com/azure/lighthouse/concepts/enterprise).
