# dbd
Diseño de Base de Datos

# Trabajo Práctico
Algebra Relacional

#1) Reportar DNI, apellido, nombre y fecha de nacimiento de empleados que realizaron reparaciones a clientes con DNI superior a: 30000000.

π Empleado.dni, Empleado.apellido, Empleado.nombre, Empleado.fechaNac (σ Empleado.nroEmp = Reparacion.nroEmp ((σ Cliente.nroCte = Reparacion.nroCte ((σ dni > 30000000 (Cliente)) ⨯ Reparacion)) ⨯ Empleado))

o

π Empleado.dni, Empleado.apellido, Empleado.nombre, Empleado.fechaNac ((pi nroEmp ((σ dni > 30000000 (Cliente)) ⨝ (Reparacion))) ⨝ Empleado)


#2) Reportar nombreT, email y teléfono de talleres con nroTaller mayor a 600."

π nombreT, email, telefono (σ nroTaller > 600 (TallerDBicicleta))



#3) Reportar DNI, apellido, nombre de aquellos clientes atendidos en el Taller con nombre ‘Y’ o que tengan reparaciones con valor superior a 1000.

pi Cliente.dni, Cliente.apellido, Cliente.nombre (sigma Cliente.nroCte = Reparacion.nroCte (Cliente ⨯ sigma Reparacion.nroEmp = Empleado.nroEmp (Reparacion ⨯ (Empleado ⨝ sigma nombreT = 'Y' (TallerDBicicleta))))) ∪ pi Cliente.dni, Cliente.apellido, Cliente.nombre ((sigma valor > 1000 (Reparacion)) ⨝ Cliente)

#o mejor versión (cambia dos sigma por productos naturales)

pi Cliente.dni, Cliente.apellido, Cliente.nombre (Cliente ⨝ pi nroCte (Reparacion ⨝ (Empleado ⨝ sigma nombreT = 'Y' (TallerDBicicleta)))) ∪ pi Cliente.dni, Cliente.apellido, Cliente.nombre ((sigma valor > 1000 (Reparacion)) ⨝ Cliente)



#4) Reportar el DNI y nombre de los empleados que no hayan participado en ningún arreglo.

pi dni, nombre ((pi nroEmp (Empleado) - pi nroEmp (Reparacion)) ⨝ (Empleado))


#5) Borrar al empleado con nroEmp: 6.

#Faltaría reasignarlo a empleado con <= (no encontré como hacerlo en el engine provisto)
Empleado - (sigma nroEmp = 6 (Empleado))
