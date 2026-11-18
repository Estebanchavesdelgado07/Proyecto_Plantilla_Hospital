# Proyecto_Plantilla_Hospital
Es un proyecto final a realizar para el curso de Programacion 
Planilla De Hospital

Esteban Chaves Delgado/208760525

## Arquitectura del Proyecto

El sistema implementa una separación de responsabilidades en capas y estructuras dinámicas propias:
**Entidades y Polimorfismo:** Clase abstracta `Empleado` con especializaciones en `Medico`, `Enfermero` y `Administrador`, además de `Departamento`, `Puesto` y `ComprobantePago`.
* **Estructuras de Datos:** Listas enlazadas simples dinámicas (`ListaEmpleado`, `ListaDepartamento`, `ListaPuesto`, `ListaPago`).
* **Controlador (`Hospital`):** Centraliza las listas maestras, aplica las reglas de negocio y coordina el cálculo de salarios brutos, deducciones de ley e impuesto sobre la renta.
* **Persistencia (`GestorArchivos`):** Serializa y reconstruye los objetos y sus relaciones desde `empleados.txt`, `departamentos.txt`, `puestos.txt` y `comprobantes.txt`.
* **Interfaz (`Interfaz`):** Gestiona los menús interactivos en consola desacoplados de la lógica interna.

---

## Instrucciones de Compilación y Ejecución

### Requisitos Previos
* Compilador de C++ con soporte para el estándar **C++11** o superior (`g++`, MinGW, Clang o MSVC).

Ubíquese en la carpeta raíz donde se encuentran los archivos `.h` y `.cpp` y ejecute:

Para ejecutar el programa:
Windows:PlanillaHospital.exe
Linux y MacOs:./PlanillaHospital

**Guia Ejecutiva**
1. Gestión de Departamentos y Puestos (Paso inicial recomendado)Crear Departamento: Registre las áreas del hospital (ej. Emergencias, Cirugía, Administración). No se permiten nombres duplicados.Agregar Puesto a un Departamento: Asocie cargos específicos (con salario asignado y responsabilidades) a un departamento existente.   Consultar / Listar / Eliminar: Permite inspeccionar departamentos con sus puestos asociados o eliminar registros.
2. Gestión de EmpleadosRegistrar Empleado: Permite ingresar personal bajo tres perfiles con cálculos salariales diferenciados:Médico: Calcula salario base + horas extra + guardias + horas nocturnas; registra especialidad y subespecialidad.   Enfermero: Calcula salario base + horas extra + guardias + horas nocturnas; registra departamento y turno.   Administrador: Calcula salario base + horas extra + horas nocturnas + bono porcentual según nivel de acceso (20% nivel 1, 25% nivel 2, 30% nivel 3); registra número de oficina. Consultar / Listar / Eliminar: Búsqueda directa por ID único, visualización detallada con cálculo de salario neto o eliminación del registro.
3. Gestión de Planilla (Comprobantes de Pago)Generar Comprobante de Pago: Solicita número de comprobante, fecha, ID de empleado y nombre del departamento. El sistema calcula automáticamente:Salario Bruto (según el tipo de empleado).   Deducciones (10.83% de cargas sociales + impuesto sobre la renta escalonado)[cite: 1, 5, 7].Salario Neto (Salario Bruto - Deducciones).   Consultar / Listar / Eliminar: Permite auditar comprobantes emitidos por número de comprobante.
4. Persistencia y Cierre Seguro
Opción 4 (Guardar datos manualmente): Fuerza el volcado inmediato de todas las listas en memoria hacia los archivos .txt sin cerrar el programa.

Opción 5 (Guardar y Salir): Guarda todos los cambios realizados en empleados.txt, departamentos.txt, puestos.txt y comprobantes.txt y libera la memoria dinámica antes de finalizar.

Nota: Utilice siempre la opción 5 para salir del sistema y garantizar la persistencia de los datos. Evite usar el carácter | al ingresar textos, ya que funciona como delimitador interno en los archivos de almacenamiento.
