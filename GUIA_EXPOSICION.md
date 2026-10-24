# Guion para presentar FarmaControl

Duración sugerida: 5 a 7 minutos. Es una propuesta para organizar la explicación; la consigna compartida no fija una duración.

## Preparación

1. Abrir https://sebastiandcpa.github.io/farmacontrol-diars/ en una computadora.
2. Entrar con el perfil **Administrador**. No se necesita contraseña porque es una demostración.
3. Utilizar los registros iniciales del sitio para el recorrido. Cada navegador conserva sus propios cambios.
4. Grabar la pantalla con el navegador visible y el micrófono del expositor. Usar los datos ficticios incluidos.

## Inicio y propósito

Mostrar la pantalla de ingreso.

“Nuestro proyecto se llama FarmaControl. Es una propuesta de sistema web para organizar las ventas, las compras y el inventario de una farmacia. Su objetivo es facilitar el seguimiento de las existencias y los vencimientos y ayudar al administrador a consultar las operaciones del negocio.”

“Esta versión es una demostración interactiva. Los cambios se guardan en el navegador. El diseño de la base de datos en SQL Server se entrega en el repositorio como un script independiente; esta demo todavía no se conecta a él.”

## Roles y resumen

Entrar como Administrador y mostrar Resumen.

“Se han considerado cuatro roles. El administrador supervisa las operaciones y administra perfiles; el cajero trabaja con clientes y ventas; el almacenero registra compras, medicamentos y lotes; y el químico farmacéutico registra referencias de recetas y revisa alertas.”

“El resumen presenta las ventas del día, el número de medicamentos, las unidades disponibles y las alertas. Los indicadores se calculan con los datos de muestra y se actualizan después de las operaciones.”

## Inventario y compra

1. Abrir **Inventario**, buscar Paracetamol y señalar el lote **P-2401**. Anotar su stock visible.
2. Abrir **Compras → Registrar compra**.
3. Seleccionar Distribuidora Salud Perú, usar el documento sugerido y el lote P-2401, cantidad **10**, costo **5.00**.
4. Confirmar y volver a Inventario para mostrar el incremento de 10 unidades.

“Cada medicamento puede tener varios lotes. En cada lote se registra su código, vencimiento, stock actual y stock mínimo. La compra registra el ingreso de mercadería y aumenta las existencias del lote seleccionado.”

## Cliente, venta y comprobante

1. Mostrar **Clientes** y explicar el registro por DNI o RUC. Se puede crear un cliente ficticio antes de continuar.
2. Abrir **Ventas → Registrar venta**.
3. Agregar **dos unidades de Paracetamol, lote P-2401**.
4. Seleccionar María Torres, tipo **Boleta de muestra** y dejar la receta sin seleccionar, ya que este producto de muestra no la requiere.
5. Confirmar: el total es **S/ 17.00**. Mostrar el comprobante y cerrar la ventana.
6. Volver a Inventario para comprobar el descuento de dos unidades.

“La venta relaciona al cliente con los productos y lotes vendidos. El sistema calcula el total usando el precio del catálogo, descuenta las unidades y conserva el detalle. Se puede visualizar o imprimir una constancia interna simulada; no es un comprobante tributario válido.”

## Validaciones y anulaciones

“Se impide vender más unidades de las disponibles, utilizar lotes vencidos o registrar documentos de compra duplicados para el mismo proveedor. Los productos marcados con receta necesitan una referencia registrada, vigente y del mismo cliente. Esto no reemplaza la revisión profesional de su contenido.”

Opcional: en la nueva venta, agregar Amoxicilina, seleccionar María Torres y confirmar sin receta para mostrar el mensaje. Seleccionar **REC-00041** si se quiere completar la operación.

“El administrador también puede anular una venta. La venta se conserva en el historial con estado anulada y las unidades se restituyen al lote original una sola vez.”

Para mostrarlo: en Ventas, usar el icono de anulación de la última operación y confirmar; luego revisar el inventario.

## Alertas y reportes

Mostrar Alertas, después Reportes.

“Las alertas identifican lotes sin existencias, productos por debajo del mínimo y lotes próximos a vencer dentro de 30 días. Los vencidos se distinguen y no pueden venderse.”

“Los reportes permiten filtrar por fecha y consultar importes, operaciones, unidades y productos más vendidos. Las ventas anuladas se excluyen de los totales. También se puede descargar la tabla en CSV.”

## Stack y arquitectura

Mostrar el repositorio público y las secciones de arquitectura de los informes entregados.

“Esta demo se construyó con HTML5 para la estructura, CSS3 para el diseño y JavaScript con módulos ES para la lógica. Utiliza localStorage para conservar los cambios en el navegador y GitHub Pages para publicar el enlace. No requiere instalar programas para abrirla.”

“El código separa las pantallas de las reglas del negocio. El modelo de datos del proyecto utiliza SQL Server, con 13 tablas como Cliente, Medicamento, Lote, Compra, Venta y MovimientoStock. El script incluye procedimientos para registrar compras, ventas y anulaciones, y vistas para consultar stock, alertas y ventas por día.”

Abrir el modelo lógico o descargar el script si se quiere mostrar esa evidencia.

## Cierre

“Con FarmaControl buscamos relacionar las operaciones comerciales con el control del inventario. Esta entrega demuestra la navegación y las reglas principales con información ficticia. La siguiente etapa para una versión conectada es incorporar un backend con autenticación y autorización reales y enlazarlo con SQL Server.”

No presentar localStorage como SQL Server ni la selección de perfil como autenticación real. No afirmar que el porcentaje de avance de la aplicación conectada ya fue certificado por esta demo.
