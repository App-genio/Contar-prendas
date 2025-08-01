Registro de Recepción de Mercadería
Esta es una aplicación web simple para llevar el registro de la recepción de mercadería, permitiendo a un usuario registrar detalles del producto, tallas y cantidades, y exportar los datos a un archivo Excel (CSV). Los datos se guardan en una base de datos de Firestore.

Estructura del Proyecto
El proyecto consta de un único archivo index.html que contiene todo el código necesario: la estructura HTML, los estilos CSS (con Tailwind CSS), y la lógica JavaScript.

Requisitos
Para utilizar esta aplicación, necesitas:

Una cuenta de GitHub para alojar los archivos.

Un proyecto de Firebase con Firestore habilitado para almacenar los datos.

Configuración de Firebase
El código de la aplicación se conecta a una base de datos de Firestore. Para que la aplicación funcione en tu propio servidor, deberás asegurarte de que la configuración de Firebase esté correcta.

Configuración requerida en la consola de Firebase:

Autenticación Anónima:

Ve a Authentication > Sign-in method.

Habilita el proveedor Anonymous.

Reglas de Seguridad de Firestore:

Ve a Firestore Database > Rules.

Reemplaza el código existente con las siguientes reglas para asegurar que cada usuario solo pueda acceder a sus propios datos:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /artifacts/{appId}/users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}

Cómo Usar
Copia y guarda el contenido del Canvas index.html en un archivo con ese mismo nombre.

Crea un nuevo archivo llamado README.md y copia el contenido de este Canvas.

Sube ambos archivos a tu repositorio de GitHub.

Abre el archivo index.html en tu navegador.

Llena los campos y usa los botones para registrar, exportar o borrar datos.

¡Esperamos que esta aplicación sea de gran ayuda para tu proceso de recepción de mercadería!