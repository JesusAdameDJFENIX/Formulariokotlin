Este código XML define una pantalla en una aplicación Android con una serie de elementos dispuestos verticalmente. Aquí está lo que cada parte hace:

<LinearLayout>: Es el contenedor principal. Organiza todos los elementos dentro de él de arriba hacia abajo, en una columna. También agrega un poco de espacio alrededor de los bordes (padding).

<EditText>: Estos son campos de entrada de texto donde los usuarios pueden escribir información. Hay tres:

Nombre: Para ingresar el nombre de la persona.
Correo Electrónico: Para ingresar la dirección de correo electrónico.
Número de Teléfono: Para ingresar el número de teléfono.
Cada uno tiene un hint que muestra un texto de ejemplo cuando el campo está vacío.

Este es el codigo .xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/editTextName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nombre"
        android:inputType="textPersonName" />

    <EditText
        android:id="@+id/editTextEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Correo Electrónico"
        android:inputType="textEmailAddress" />

    <EditText
        android:id="@+id/editTextPhone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Número de Teléfono"
        android:inputType="phone" />

    <ImageView
        android:id="@+id/imageViewProfile"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:src="@drawable/default_image"
        android:contentDescription="Imagen de perfil" />

    <Button
        android:id="@+id/buttonSubmit"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Enviar" />
</LinearLayout>

<ImageView>: Muestra una imagen. En este caso, se usa para mostrar una imagen de perfil con un tamaño fijo. La imagen que aparece por defecto es default_image.

<Button>: Un botón que dice "Enviar". Los usuarios pueden presionar este botón para enviar o confirmar la información que han ingresado.

Todo está organizado de manera que sea fácil para el usuario ingresar su información y ver la imagen de perfil antes de enviar el formulario.
![lol](https://github.com/user-attachments/assets/d1a04716-ece5-49a9-9b1f-bd2bd0d0ea4f)

a continuacion explicaremos el .kt
Importaciones: Estas líneas traen clases necesarias para la funcionalidad:

Bundle, Button, EditText, ImageView, Toast para la interfaz de usuario.
AppCompatActivity para crear actividades compatibles con versiones anteriores de Android.
Clase MainActivity: Es la actividad principal de la aplicación, que hereda de AppCompatActivity. Esto significa que es una pantalla o vista en tu aplicación.

Método onCreate:

super.onCreate(savedInstanceState): Llama al método onCreate de la clase base para asegurarse de que se inicialice correctamente.
setContentView(R.layout.activity_main): Establece el diseño de la actividad usando el archivo XML activity_main.xml.
Referencias a Vistas:

val editTextName, val editTextEmail, val editTextPhone: Obtiene las referencias a los campos de entrada de texto del diseño para poder interactuar con ellos.
val imageViewProfile: Obtiene la referencia a la vista de imagen para mostrar y cambiar la imagen.
val buttonSubmit: Obtiene la referencia al botón que los usuarios presionan para enviar el formulario.
Configurar el Botón:

buttonSubmit.setOnClickListener { ... }: Establece un listener para el botón, que es un bloque de código que se ejecuta cuando el botón es presionado.
Dentro del listener:
val name, val email, val phone: Obtiene el texto ingresado en los campos de texto.
Verifica si alguno de los campos está vacío. Si es así, muestra un mensaje de advertencia usando Toast (una pequeña notificación que aparece en la pantalla).
Si todos los campos están llenos, cambia la imagen en imageViewProfile a una nueva imagen (R.drawable.new_image) y muestra un mensaje de éxito.

este es el código .kt
package com.example.formulario

import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.ImageView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val editTextName = findViewById<EditText>(R.id.editTextName)
        val editTextEmail = findViewById<EditText>(R.id.editTextEmail)
        val editTextPhone = findViewById<EditText>(R.id.editTextPhone)
        val imageViewProfile = findViewById<ImageView>(R.id.imageViewProfile)
        val buttonSubmit = findViewById<Button>(R.id.buttonSubmit)

        buttonSubmit.setOnClickListener {
            val name = editTextName.text.toString()
            val email = editTextEmail.text.toString()
            val phone = editTextPhone.text.toString()

            if (name.isEmpty() || email.isEmpty() || phone.isEmpty()) {
                Toast.makeText(this, "Todos los campos deben ser completados", Toast.LENGTH_SHORT).show()
            } else {
                // Cambiar la imagen de manera dinámica
                imageViewProfile.setImageResource(R.drawable.new_image)
                Toast.makeText(this, "Formulario enviado con éxito", Toast.LENGTH_SHORT).show()
            }
        }
    }
}

![Captura de pantalla 2024-09-15 232356](https://github.com/user-attachments/assets/c275a18b-19cf-4ce6-9090-9998cddceb62)

y por ultimo ese es el resultado final

![lol](https://github.com/user-attachments/assets/87368ec9-220b-4691-9d76-bae6b08d957c)


