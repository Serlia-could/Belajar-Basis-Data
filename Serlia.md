# Belajar-Basis-Data
Server [localhost]:
Database [postgres]:
Port [5432]:
Username [postgres]:
Password for user postgres:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# create database siakad
postgres-# ;
CREATE DATABASE
postgres=#
postgres=#
postgres=#
postgres=# \l
                                                                    List of databases
   Name    |  Owner   | Encoding | Locale Provider |          Collate           |           Ctype            | Locale | ICU Rules |   Access privileges
-----------+----------+----------+-----------------+----------------------------+----------------------------+--------+-----------+-----------------------
 caffe     | postgres | UTF8     | libc            | English_United States.1252 | English_United States.1252 |        |           |
 postgres  | postgres | UTF8     | libc            | English_United States.1252 | English_United States.1252 |        |           |
 siakad    | postgres | UTF8     | libc            | English_United States.1252 | English_United States.1252 |        |           |
 sisfo     | postgres | UTF8     | libc            | English_United States.1252 | English_United States.1252 |        |           |
 sisfo24   | postgres | UTF8     | libc            | English_United States.1252 | English_United States.1252 |        |           |
 template0 | postgres | UTF8     | libc            | English_United States.1252 | English_United States.1252 |        |           | =c/postgres          +
           |          |          |                 |                            |                            |        |           | postgres=CTc/postgres
 template1 | postgres | UTF8     | libc            | English_United States.1252 | English_United States.1252 |        |           | =c/postgres          +
           |          |          |                 |                            |                            |        |           | postgres=CTc/postgres
(7 rows)


postgres=# \c siakad
You are now connected to database "siakad" as user "postgres".
siakad=# create table mahasiswa
siakad-# (
siakad(# nim char(8) primary key, nama varchar(30), alamat varchar(75)
siakad(# )
siakad-# ;
CREATE TABLE
siakad=# \d
           List of relations
 Schema |   Name    | Type  |  Owner
--------+-----------+-------+----------
 public | mahasiswa | table | postgres
(1 row)


siakad=# insert into mahasiswa values
siakad-# ('D0424312', 'Serlia', 'Toraja'),('D04245022', 'hasanah', 'Maloga')
siakad-# ;
ERROR:  value too long for type character(8)
siakad=# insert into mahasiswa values
siakad-# ('D0424312', 'Serlia', 'Toraja'),('D0424502', 'Hasanah', 'Maloga')
siakad-# ;
INSERT 0 2
siakad=# select * from mahasiswa
siakad-# ;
   nim    |  nama   | alamat
----------+---------+--------
 D0424312 | Serlia  | Toraja
 D0424502 | Hasanah | Maloga
(2 rows)


siakad=# UPDATE MAHASISWA
siakad-# SET alamat='Majene'
siakad-# WHERE nim='D0424312'
siakad-# ;
UPDATE 1
siakad=# select * from mahasiswa
siakad-# ;
   nim    |  nama   | alamat
----------+---------+--------
 D0424502 | Hasanah | Maloga
 D0424312 | Serlia  | Majene
(2 rows)


siakad=# delet from MAHASISWA
siakad-# where alamat='Maloga';
ERROR:  syntax error at or near "delet"
LINE 1: delet from MAHASISWA
        ^
siakad=# delet from MAHASISWA where nim ='D0424312';
ERROR:  syntax error at or near "delet"
LINE 1: delet from MAHASISWA where nim ='D0424312';
        ^
siakad=# delete from MAHASISWA where nim ='D0424312';
DELETE 1
siakad=# select * from mahasiswa
siakad-# ;
   nim    |  nama   | alamat
----------+---------+--------
 D0424502 | Hasanah | Maloga
(1 row)


siakad=# insert from MAHASISWA where nim ='D0424312';
ERROR:  syntax error at or near "from"
LINE 1: insert from MAHASISWA where nim ='D0424312';
               ^
siakad=# insert from MAHASISWA where nim ='D0424309';
ERROR:  syntax error at or near "from"
LINE 1: insert from MAHASISWA where nim ='D0424309';
               ^
siakad=# insert into mahasiswa values
siakad-# ('D0424315', 'Fina', 'Majene'),('D0424507', 'arif', 'pw')
siakad-# ;
INSERT 0 2
siakad=#  select * from mahasiswa
siakad-# ;
   nim    |  nama   | alamat
----------+---------+--------
 D0424502 | Hasanah | Maloga
 D0424315 | Fina    | Majene
 D0424507 | arif    | pw
(3 rows)


siakad=#
