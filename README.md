# dbd
Diseño de Base de Datos

# Trabajo Práctico
Algebra Relacional

#Reportar DNI, apellido, nombre y fecha de nacimiento de empleados que realizaron reparaciones a
#clientes con DNI superior a: 30000000.

π Empleado.dni, Empleado.apellido, Empleado.nombre, Empleado.fechaNac (σ Empleado.nroEmp = Reparacion.nroEmp ((σ Cliente.nroCte = Reparacion.nroCte ((σ dni > '30000000' (Cliente)) ⨯ Reparacion)) ⨯ Empleado))

#Reportar nombreT, email y teléfono de talleres con nroTaller mayor a 600."
#Error pq considera los strings '7' '8' '9' como mayores que '600'. Hay que modificar la bbdd para que la variable nroTaller sea un
#numero

π nombreT, email, telefono (σ nroTaller > '600' (TallerDBicicleta))
