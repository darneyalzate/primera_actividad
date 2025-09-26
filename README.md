CREATE DATABASE AGENCIA_VIAJE;

USE AGENCIA_VIAJE;

CREATE TABLE CLIENTES(
 id INT AUTO_INCREMENT PRIMARY KEY ,
 nombre_completo VARCHAR(40) not null,
 tipo_documento VARCHAR(15) NOT NULL,
 telefono INT(10) not null UNIQUE,
 direccion VARCHAR(40) not null,
 correo VARCHAR(40) not null
 
 );
 
DESCRIBE CLIENTES;
 
CREATE TABLE DESTINO_VIAJE(
 id INT AUTO_INCREMENT PRIMARY KEY,
 nacional VARCHAR (10) NOT NULL,
 internacional VARCHAR (10) NOT NULL

);


DESCRIBE DESTINO_VIAJE;
 

CREATE TABLE NUMERO_PASAJEROS(
 id INT AUTO_INCREMENT PRIMARY KEY,
 nombre_completo VARCHAR(40) not null,
 tipo_documento VARCHAR (15) NOT NULL,
 edad int (10) not NULL 
 
);
 
DESCRIBE NUMERO_PASAJEROS;


CREATE TABLE DESTINO_TURISTICO(
 id INT AUTO_INCREMENT PRIMARY KEY,
 nombre_lugares VARCHAR (30) NOT NULL,
 ubicacion_turistico VARCHAR (30) NOT NULL
 
);
 
DESCRIBE DESTINO_TURISTICO;

 
CREATE TABLE INFO_VUELOS(
 id INT AUTO_INCREMENT PRIMARY KEY,
 numero_vuelo VARCHAR (20) NOT NULL 

);

DESCRIBE INFO_VUELOS;

 
CREATE TABLE PAQUETES(
 id INT AUTO_INCREMENT PRIMARY KEY,
 codigo_unico INT (10) not null unique,
 disponibilidad VARCHAR (10) not NULL ,
 fecha_salida DATETIME	not null,
 precio DECIMAL (20) not null,
 duracion INT (10) not null,
 actividad_incluida VARCHAR (10) NOT NULL,
 id_pasajero int,
 FOREIGN KEY (id_pasajero) REFERENCES NUMERO_PASAJEROS(id)
 
 );
 
DESCRIBE PAQUETES;


CREATE TABLE RESERVA(
 id int AUTO_INCREMENT PRIMARY KEY,
 codigo_unico INT (10) not null unique,
 fecha_reserva DATETIME NOT NULL,
 estado_reserva VARCHAR (20) NOT NULL,
 detalle_pago VARCHAR (20) NOT NULL,
 paquete_selecionado VARCHAR (20) NOT NULL,
 id_vuelo int,
 id_destino int,
 id_cliente int,
 FOREIGN KEY (id_vuelo) REFERENCES INFO_VUELOS(id),
 FOREIGN KEY (id_destino) REFERENCES DESTINO_VIAJE(id),
 FOREIGN KEY (id_cliente) REFERENCES CLIENTES(id)
 
 );
 
DESCRIBE RESERVA;

CREATE TABLE GUIAS_TURISTICOS(
 id int AUTO_INCREMENT PRIMARY KEY,
 id_guias INT (10) UNIQUE NOT NULL,
 nombre_completo VARCHAR(40) not null,
 tipo_documento VARCHAR (11) NOT NULL,
 idioma_hablar VARCHAR (20) NOT NULL,
 id_destino int,
 FOREIGN KEY (id_destino) REFERENCES DESTINO_TURISTICO(id)

);
 
DESCRIBE GUIAS_TURISTICOS;
