---
title: Treffen von Vorhersagen mit der Machine Learning-Erweiterung
titleSuffix: Azure Data Studio
description: Hier erfahren Sie, wie Sie die Machine Learning-Erweiterung für Azure Data Studio verwenden, um mit einem ONNX-Modell in Ihrer Datenbank Vorhersagen zu treffen.
ms.date: 06/09/2020
ms.reviewer: sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 5472f4ff32a807b58091fd56f3382aa73ead142e
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88745490"
---
# <a name="make-predictions-with-machine-learning-extension-preview-for-azure-data-studio"></a>Treffen von Vorhersagen mit der Machine Learning-Erweiterung (Vorschauversion) für Azure Data Studio

Hier erfahren Sie, wie Sie die [Machine Learning-Erweiterung für Azure Data Studio](machine-learning-extension.md) verwenden, um mit einem ONNX-Modell in Ihrer Datenbank Vorhersagen zu treffen. Die Erweiterung generiert mithilfe von [PREDICT](../t-sql/queries/predict-transact-sql.md) ein T-SQL-Skript, um mit einem zuvor importierten Modell, einem Modell aus einer lokalen Datei oder aus Azure Machine Learning Vorhersagen für das in Ihrer Tabelle gespeicherte Dataset zu treffen.

> [!IMPORTANT]
> Das Treffen von Vorhersagen mit der Machine Learning-Erweiterung unterstützt derzeit nur [Machine Learning Services in Azure SQL Managed Instance](/azure/azure-sql/managed-instance/machine-learning-services-overview) und [Azure SQL Edge mit ONNX](/azure/azure-sql-edge/onnx-overview).

## <a name="prerequisites"></a>Voraussetzungen

- Installieren und konfigurieren Sie die [Machine Learning-Erweiterung für Azure Data Studio](machine-learning-extension.md). Sie müssen die [Python-Installationspfade in den Erweiterungseinstellungen](machine-learning-extension.md#settings) angeben.

- Sie benötigen die Python-Pakete **onnxruntime**, **mlflow** und **mlflow-dbstore**. Wenn die Pakete nicht bereits installiert sind, werden Sie von der Machine Learning-Erweiterung dazu aufgefordert, diese zu installieren.

## <a name="make-predictions-from-onnx-model"></a>Treffen von Vorhersagen mit dem ONNX-Modell

Führen Sie die folgenden Schritte durch, um mithilfe eines ONNX-Modells Vorhersagen zu treffen.

1. Klicken Sie auf **Vorhersagen treffen**.

1. Wenn Sie zur Installation von **onnxruntime**, **mlflow** und **mlflow-dbstore** aufgefordert werden, klicken Sie auf **Ja**.

1. Wählen Sie den Speicherort des Modells aus, und klicken Sie auf **Weiter**. Verwenden Sie Folgendes:
    - **Importierte Modelle:** Wählen Sie diese Option aus, um ein Modell zu verwenden, das bereits in Ihrer Datenbank gespeichert ist. Wählen Sie die **Modelldatenbank** und die **Modelltabelle** aus, in der Ihr Modell gespeichert ist. Wählen Sie das gewünschte Modell aus, und klicken Sie auf **Weiter**.
    - **Dateiupload:** Wählen Sie diese Option aus, um ein Modell aus einer Datei zu verwenden. Wählen Sie die Modelldatei unter **Quelldateien** aus, und klicken Sie auf **Weiter**.
    - **Azure Machine Learning:** Wählen Sie diese Option aus, um ein Modell aus Azure Machine Learning zu verwenden. Zunächst müssen Sie sich **bei Azure anmelden**. Wählen Sie dann Ihr **Azure-Konto**, Ihr **Azure-Abonnement**, Ihre **Azure-Ressourcengruppe** und Ihren **Azure ML-Arbeitsbereich** aus. Wählen Sie das gewünschte Modell aus, und klicken Sie auf **Weiter**.

1. Ordnen Sie Ihrem Modell die Quelldaten zu.
    - Wählen Sie die **Quelldatenbank** und die **Quelltabelle** mit dem Dataset aus, für das Sie die Vorhersage treffen möchten.
    - Ordnen Sie die Spalten unter **Model Input mapping** (Zuordnung der Modelleingabe) und **Model output** (Modellausgabe) zu. Die Erweiterung ordnet automatisch Spalten mit dem gleichen Namen und dem gleichen Datentyp zu.

1. Klicken Sie auf **Vorhersagen**.

Azure Data Studio erstellt mit [PREDICT](../t-sql/queries/predict-transact-sql.md) eine neue T-SQL-Abfrage, mit der Sie Vorhersagen für Ihre Daten treffen können.

## <a name="next-steps"></a>Nächste Schritte

- [Machine Learning-Erweiterung in Azure Data Studio](machine-learning-extension.md)
- [Verwalten von Paketen in der Datenbank](machine-learning-extension-manage-packages.md)
- [Importieren und Anzeigen von Modellen](machine-learning-extension-import-view-models.md)
- [Notebooks in Azure Data Studio](notebooks-guidance.md)
- [SQL Machine Learning-Dokumentation](../machine-learning/index.yml)
- [Machine Learning Services in Azure SQL Managed Instance (Vorschauversion)](/azure/azure-sql/managed-instance/machine-learning-services-overview)
- [Machine Learning und KI mit ONNX in SQL Edge (Vorschau)](/azure/azure-sql-edge/onnx-overview)
