# Tienda Online con Svelte: Carrito de Compras en Tiempo Real

### Dependencias
```
npm i bootstrap@5.3.3
npm i bootstrap-icons
```

## Descripción

Esta es una tienda en línea de café, donde los usuarios pueden agregar productos a su carrito, ver el subtotal de su pedido y enviarlo a través de WhatsApp. La aplicación está desarrollada con Svelte y utiliza Bootstrap para el diseño.

## Características

- **Interfaz de usuario dinámica**: Los productos se muestran en una interfaz de usuario moderna y amigable.
- **Carrito de compras**: Los usuarios pueden agregar productos al carrito, ver detalles de los productos y eliminarlos.
- **Envío por WhatsApp**: Los usuarios pueden enviar sus pedidos directamente a través de WhatsApp.
- **Responsive**: La aplicación se adapta a diferentes tamaños de pantalla para brindar una experiencia fluida en dispositivos móviles y de escritorio.

## Tecnologías utilizadas

- **Svelte**: Framework utilizado para el desarrollo del frontend.
- **Bootstrap**: Framework CSS utilizado para el diseño y la responsividad.
- **JavaScript**: Lenguaje principal para la interacción de la aplicación.
- **Svelte Store**: Se usa para gestionar el estado global del carrito y el mensaje de WhatsApp.
- **Font Awesome**: Para los íconos, como el de la bolsa de compras y el de la basura.

## Estructura de la Aplicación

```
src/
├── lib/
│   ├── Api.svelte         # Componente para manejar la API de productos
│   └── Footer.svelte      # Componente para el pie de página
├── stores/
│   ├── cartStore.js       # Store para gestionar el carrito de compras
│   └── whatsappStore.js   # Store para generar el mensaje de WhatsApp
├── App.svelte             # Componente principal de la aplicación
├── main.js                # Archivo de entrada
└── public/
    └── fotos-cafe/        # Imágenes de los productos
```

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/tuusuario/tienda-cafe.git
```

### 2. Instalar dependencias

Asegúrate de tener Node.js y npm instalados, luego instala las dependencias del proyecto.

```bash
cd tienda-cafe
npm install
```

### 3. Ejecutar la aplicación

Para ejecutar la aplicación en modo de desarrollo, usa el siguiente comando:

```bash
npm run dev
```

La aplicación estará disponible en `http://localhost:5000`.

## Uso

1. Los productos de la tienda se muestran en la interfaz principal.
2. Los usuarios pueden agregar productos al carrito con un solo clic.
3. El carrito puede ser visualizado desde el ícono en la esquina superior derecha.
4. Los usuarios pueden ver el subtotal y eliminar productos del carrito.
5. Una vez que los productos estén listos, pueden enviar el pedido directamente a través de WhatsApp.

## Contribuciones

Las contribuciones son bienvenidas. Si deseas agregar nuevas características o corregir errores, sigue estos pasos:

1. Haz un fork del proyecto.
2. Crea una rama nueva para tu característica (`git checkout -b nueva-caracteristica`).
3. Haz tus cambios y commitea (`git commit -am 'Añadir nueva característica'`).
4. Haz push a tu rama (`git push origin nueva-caracteristica`).
5. Abre un Pull Request en GitHub.

## Licencia

Este proyecto está licenciado bajo la [MIT License](https://opensource.org/licenses/MIT).

## Contacto

Puedes ponerte en contacto conmigo a través de mi correo electrónico: `tu-email@dominio.com`.

