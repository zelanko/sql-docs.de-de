---
description: Implizit zugewiesene Deskriptoren
title: Implizit zugeordnete Deskriptoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5daa7f622798e1394c186b333069933b48e367af
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461422"
---
# <a name="implicitly-allocated-descriptors"></a>Implizit zugewiesene Deskriptoren
Wenn ein Anweisungs Handle zugeordnet ist, ordnet die Anwendung implizit einen Satz von vier Deskriptoren zu. Die Anwendung kann die Handles dieser implizit zugeordneten Deskriptoren als Attribute des Anweisungs Handles abrufen. Wenn die Anwendung das Anweisungs Handle freigibt, gibt der Treiber alle implizit zugewiesenen Deskriptoren für dieses Handle frei.
