# Quête LVM

Le challenge consiste, en partant d'une machine debian telle que celle installée au début de cette quête, à suivre une succession d'étapes visant à effectuer des opérations classiques sur LVM.

L'ensemble des commandes et leurs affichages sont à recopier dans la solution de cette quête

<br>

## 1. Ajoute un nouveau disque à la machine et ajoute le au groupe de volume `debian-vg` pour au moins doubler l'espace du groupe de volume

* Ajoute d'un nouveau DD à la machine :
```code
fdisk -l
```
<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2001%20fdisk%20-l.png width = "450" height = "100">

<br>

```code
fdisk /dev/sdc
```
<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2002%20fdisk%20sdc.png width = "550" height = "500">

<br>

<img src=https://github.com/Fairskip/LVM/blob/main/challenge%2003%20fdis%20-l.png width = "550" height = "200">

<br>

* Création d'un PV

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2004%20pvcreate.png width = "350" height = "100">

<br>

* Ajout du PV au VG

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%205%20vgextend.png width = "300" height = "60">

<br>

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2005%20vgdisplay.png width = "600" height = "300">

<br>

## 2. Créer un snapshot de LV `home`

 ```code
lvcreate -L 12g -s -n home-snap /dev/Luva-vg/home
```

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2008%20create%20snapshot.png width = "450" height = "300">

<br>

## 3. Monte le snapshot créé sur `/home-snap`

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2009%20Mount.png width = "500" height = "50">

<br>

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2010%20df%20-h.png width = "650" height = "300">

<br>

## 4. Constate que `/home-snap` est bien une copie de `/home`

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2012%20lvdisplay.png width = "700" height = "450">

<br>

## 5. On peut alors travailler sur `/home-snap` et y faire des modifications. En supposant qu'on a maintenant plus besoin de la copie, démonte `/home-snap`

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2013%20Umount.png width = "500" height = "250">

<br>

## 6. Détruit le snapshot

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2014%20Remove.png width = "500" height = "60">

<br>

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2015%20lvs.png width = "300" height = "250">

<br>

<img src=https://github.com/Fairskip/LVM/blob/main/Challenge%2016%20lvdisplay.png width = "500" height = "250">
