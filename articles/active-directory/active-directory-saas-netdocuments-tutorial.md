---
title: "Tutorial: Integración de Azure Active Directory con NetDocuments | Microsoft Docs"
description: "Aprenda cómo usar NetDocuments con Azure Active Directory para habilitar el inicio de sesión único, el aprovisionamiento automatizado, etc."
services: active-directory
author: jeevansd
documentationcenter: na
manager: femila
ms.assetid: 1a47dc42-1a17-48a2-965e-eca4cfb2f197
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 03/24/2017
ms.author: jeedes
translationtype: Human Translation
ms.sourcegitcommit: eeb56316b337c90cc83455be11917674eba898a3
ms.openlocfilehash: a6ca819329de130257ec67e63a53f87cbca9f39b
ms.lasthandoff: 04/03/2017


---
# <a name="tutorial-azure-active-directory-integration-with-netdocuments"></a>Tutorial: Integración de Azure Active Directory con NetDocuments
El objetivo de este tutorial es mostrar la integración de Azure y NetDocuments. En la situación descrita en este tutorial se supone que ya cuenta con los elementos siguientes:

* Una suscripción de Azure válida
* Un inquilino de NetDocuments

Después de completar este tutorial, los usuarios de Azure AD que ha asignado a NetDocuments podrán realizar un inicio de sesión único en la aplicación en el sitio de la compañía de NetDocuments (inicio de sesión iniciado por el proveedor de servicios) o con la [Introducción al Panel de acceso](active-directory-saas-access-panel-introduction.md).

La situación descrita en este tutorial consta de los siguientes bloques de creación:

1. Habilitación de la integración de aplicaciones para NetDocuments
2. Configuración del inicio de sesión único (SSO)
3. Configuración del aprovisionamiento de usuario
4. Asignación de usuarios

![Escenario](./media/active-directory-saas-netdocuments-tutorial/IC795040.png "Escenario")

## <a name="enabling-the-application-integration-for-netdocuments"></a>Habilitación de la integración de aplicaciones para NetDocuments
El objetivo de esta sección es describir cómo habilitar la integración de las aplicaciones para NetDocuments.

**Siga estos pasos para habilitar la integración de aplicaciones para NetDocuments:**

1. En el panel de navegación izquierdo del Portal de Azure clásico, haga clic en **Active Directory**.
   
   ![Active Directory](./media/active-directory-saas-netdocuments-tutorial/IC700993.png "Active Directory")
2. En la lista **Directory** , seleccione el directorio cuya integración desee habilitar.
3. Para abrir la vista de aplicaciones, haga clic en **Applications** , en el menú superior de la vista de directorios.
   
   ![Aplicaciones](./media/active-directory-saas-netdocuments-tutorial/IC700994.png "Aplicaciones")
4. Haga clic en **Agregar** en la parte inferior de la página.
   
   ![Agregar aplicaciones](./media/active-directory-saas-netdocuments-tutorial/IC749321.png "Agregar aplicaciones")
5. En el cuadro de diálogo **¿Qué desea hacer?**, haga clic en **Agregar una aplicación de la galería**.
   
   ![Agregar una aplicación de la galería](./media/active-directory-saas-netdocuments-tutorial/IC749322.png "Agregar una aplicación de la galería")
6. En el **cuadro de búsqueda**, escriba **NetDocuments**.
   
   ![Galería de aplicaciones](./media/active-directory-saas-netdocuments-tutorial/IC795041.png "Galería de aplicaciones")
7. En el panel de resultados, seleccione **NetDocuments** y, luego, haga clic en **Completar** para agregar la aplicación.
   
   ![NetDocuments](./media/active-directory-saas-netdocuments-tutorial/IC795042.png "NetDocuments")
   
## <a name="configure-single-sign-on"></a>Configurar inicio de sesión único

El objetivo de esta sección es describir cómo se habilita la autenticación de los usuarios en NetDocuments con su cuenta de Azure AD usando el protocolo SAML basado en la federación.  

La configuración del SSO para NetDocuments requiere la recuperación de un valor de huella digital de un certificado. Si no está familiarizado con este procedimiento, consulte [Recuperación del valor de huella digital de un certificado](http://youtu.be/YKQF266SAxI).

**Para configurar el inicio de sesión único (SSO), realice los pasos siguientes:**

1. En el Portal de Azure clásico, en la página de integración de aplicaciones de **NetDocuments**, haga clic en **Configurar inicio de sesión único** para abrir el cuadro de diálogo **Configurar inicio de sesión único**.
   
   ![Configurar inicio de sesión único](./media/active-directory-saas-netdocuments-tutorial/IC795043.png "Configurar inicio de sesión único")
2. En la página **¿Cómo desea que los usuarios inicien sesión en NetDocuments?**, seleccione **Inicio de sesión único de Microsoft Azure AD** y, luego, haga clic en **Siguiente**.
   
   ![Configurar inicio de sesión único](./media/active-directory-saas-netdocuments-tutorial/IC795044.png "Configurar inicio de sesión único")
3. En la página **Configurar dirección URL de la aplicación** , realice los pasos siguientes:
   
   ![Configurar dirección URL de la aplicación](./media/active-directory-saas-netdocuments-tutorial/IC795045.png "Configurar dirección URL de la aplicación")
   
   1. En el cuadro de texto **URL de inicio de sesión**, escriba su dirección URL que usan los usuarios para iniciar sesión en la aplicación NetDocuments (por ejemplo, "*https://vault.netvoyage.com/neWeb2/docCent.aspx?whr=CA-JI1BG3H1*").
   2. En el cuadro de texto **URL de respuesta de NetDocuments**, escriba el mismo valor que ha escrito en el cuadro de texto **URL de inicio de sesión**.  
      
      >[!NOTE]
      >Puede encontrar el valor correcto al final del cuadro de diálogo **Identidad federada** (consulte la captura de pantalla para el paso 9).
      >
      >
     
   3. Haga clic en **Siguiente**.
4. En la página **Configurar inicio de sesión único en NetDocuments**, para descargar el certificado, haga clic en **Descargar certificado** y, luego, guarde el archivo de certificado en el equipo.
   
   ![Configurar inicio de sesión único](./media/active-directory-saas-netdocuments-tutorial/IC795046.png "Configurar inicio de sesión único")
5. En otra ventana del explorador web, inicie sesión en como administrador en el sitio de la compañía de NetDocuments.
6. Vaya a **Administración**.
7. Haga clic en **Agregar y quitar usuarios y grupos**.
   
   ![Repositorio](./media/active-directory-saas-netdocuments-tutorial/IC795047.png "Repositorio")
8. Haga clic en **Configurar opciones de autenticación avanzadas**.
   
   ![Configurar opciones de autenticación avanzadas](./media/active-directory-saas-netdocuments-tutorial/IC795048.png "Configurar opciones de autenticación avanzadas")
9. En el cuadro de diálogo **Identidad federada** , realice los pasos siguientes:
   
   ![Identidad federada](./media/active-directory-saas-netdocuments-tutorial/IC795049.png "Identidad federada")
   
   1. Como **Tipo de servidor de identidad federada**, seleccione **Servicios de federación de Active Directory**.
   2. Haga clic en **Elegir archivo**para cargar el archivo de metadatos.
   3. Haga clic en **OK**.
10. En el Portal de Azure clásico, seleccione la confirmación de configuración de inicio de sesión único y haga clic en **Completar** para cerrar el cuadro de diálogo **Configurar inicio de sesión único**.
    
    ![Configurar inicio de sesión único](./media/active-directory-saas-netdocuments-tutorial/IC795050.png "Configurar inicio de sesión único")
    
## <a name="configure-user-provisioning"></a>Configurar aprovisionamiento de usuarios

Para permitir que los usuarios de Azure AD inicien sesión en NetDocuments, deben aprovisionarse en NetDocuments. En el caso de NetDocuments, el aprovisionamiento es una tarea manual.

**Siga estos pasos para configurar el aprovisionamiento de usuario:**

1. Inicie sesión como administrador en el sitio de la compañía **NetDocuments** .
2. En el menú de la parte superior, haga clic en **Administrador**.
   
   ![Administración](./media/active-directory-saas-netdocuments-tutorial/IC795051.png "Administración")
3. Haga clic en **Agregar y quitar usuarios y grupos**.
   
   ![Repositorio](./media/active-directory-saas-netdocuments-tutorial/IC795047.png "Repositorio")
4. En el cuadro de texto **Dirección de correo electrónico**, escriba la dirección de correo electrónico de la cuenta válida de Azure Active Directory que quiera aprovisionar y haga clic en **Agregar usuario**.
   
   ![Dirección de correo electrónico](./media/active-directory-saas-netdocuments-tutorial/IC795053.png "Dirección de correo electrónico")
   
   >[!NOTE]
   >El titular de la cuenta de Azure Active Directory recibirá un mensaje de correo electrónico con un vínculo para confirmar la cuenta antes de que se active.
   > 
   > 

>[!NOTE]
>Puede usar cualquier otra API o herramienta de creación de cuentas de usuario de NetDocuments ofrecida por NetDocuments para aprovisionar cuentas de usuario de AAD.
>
>

## <a name="assign-users"></a>Asignar usuarios
Para probar la configuración, debe conceder acceso a los usuarios de Azure AD a los que quiere permitir el uso de su aplicación.

**Para asignar usuarios a NetDocuments, lleve a cabo los siguientes pasos:**

1. En el Portal de Azure clásico, cree una cuenta de prueba.
2. En la página de integración de la aplicación **NetDocuments**, haga clic en **Asignar usuarios**.
   
   ![Asignar usuarios](./media/active-directory-saas-netdocuments-tutorial/IC795054.png "Asignar usuarios")
3. Seleccione su usuario de prueba, haga clic en **Asignar** y en **Sí** para confirmar la asignación.
   
   ![Sí](./media/active-directory-saas-netdocuments-tutorial/IC767830.png "Sí")

Si desea probar la configuración de inicio de sesión único (SSO), abra el panel de acceso. Para obtener más información sobre el Panel de acceso, vea [Introducción al Panel de acceso](active-directory-saas-access-panel-introduction.md).

## <a name="additional-resources"></a>Recursos adicionales

* [Lista de tutoriales sobre cómo integrar aplicaciones SaaS con Azure Active Directory](active-directory-saas-tutorial-list.md)
* [¿Qué es el acceso a aplicaciones y el inicio de sesión único con Azure Active Directory?](active-directory-appssoaccess-whatis.md)
