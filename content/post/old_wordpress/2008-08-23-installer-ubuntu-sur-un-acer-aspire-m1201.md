---
title: Installer Ubuntu sur un Acer Aspire M1201
author: Jice

date: 2008-08-23
url: /2008/08/installer-ubuntu-sur-un-acer-aspire-m1201/
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Linux
tags:
  - Linux
  - Ubuntu
---
<p align="justify">
  De nombreuses personnes auront profiter récemment d&#8217;une offre chez <a href="http://www.rueducommerce.fr/" target="_blank">Rue du Commerce</a> concernant un <a href="http://www.rueducommerce.fr/Ordinateurs/PC/PC-de-bureau-Grand-Public/ACER/438529-PC-Acer-Aspire-M1201-BM7X-Atlhon-64-X2-5000-ATI-Radeon-HD-3450-320Go-3Go.htm" target="_blank">ordinateur Acer Aspire</a>, livré sans OS. Pensant pouvoir installer facilement <strong>Ubuntu </strong>dessus, je me suis jeté dessus. Hors l&#8217;architecture du PC (AMD 64), fait qu&#8217;il faut télécharger une version dédiée de Ubuntu.
</p>

### Procédure d&#8217;installation :

<p align="justify">
  Procurez-vous la version pour architecture 64 sur le site de Ubuntu : <a href="http://www.ubuntu-fr.org/telechargement" target="_blank">http://www.ubuntu-fr.org/telechargement</a> vous pouvez aussi télécharger le torrent que j&#8217;ai utilisé pour mon installation (torrent fabriqué par ubuntu-fr : ubuntu 8.04, amd64, gnome) : <a href="doc/informatique/ubuntu-8.04.1-desktop-amd64.iso.torrent" target="_blank">torrent</a>.
</p>

<p align="justify">
  Gravez ensuite l&#8217;image du disque une fois téléchargée (téléchargement avec <a href="http://www.utorrent.com/download.php" target="_blank">u torrent</a> par exemple, et gravure avec <a href="http://infrarecorder.sourceforge.net/" target="_blank">Infra Recorder</a> <<&#8211; ces deux logiciels sont pour les utilisateurs windows).
</p>

<p align="justify">
  Redémarrer votre ordinateur avec le CD gravé dans le lecteur, la procédure de boot commence (si votre BIOS est bien configuré). Lors du premier Splash screen, choisissez l&#8217;option F6 -> <strong>ACPI=OFF</strong> (pressez 2 fois F6 pour voir l&#8217;option, &#8220;entrer&#8221; pour sélectionner, et &#8220;echap&#8221; pour revenir au menu principal). Sans celà, vous aurez un petit message d&#8217;erreur qui empêchera l&#8217;installation.
</p>

<p align="justify">
  <h3>
    Lancez le système correctement :
  </h3>
  
  <p>
    Si vous lancez le système tel quel après l&#8217;installation, vous retrouverez le petit message d&#8217;erreur obtenu si vous aviez tenté l&#8217;installation sans &#8220;ACPI OFF&#8221;. Nous allons donc devoir modifier légèrement la procédure de démarrage de Ubuntu.
  </p>
  
  <p>
    Redémarrez avec le CD, en mode Live CD et avec l&#8217;option ACPI=OFF.
  </p>
  
  <p align="justify">
    Une fois Ubuntu Live lancé, rendez-vous sur le disque dur (là où se trouve installé Ubuntu). Parcourez vos emplacement, et trouvez le fichier <strong>menu.lst </strong>dans le répertoire /boot/grub (chez moi il se trouve à : /media/disk/boot/grub). Notez son emplacement. Ouvrez alors une console, et tapez :
  </p>
  
  <blockquote>
    <p>
      <em>sudo gedit /media/disk/boot/grub/menu.lst</em>
    </p>
  </blockquote>
  
  <p>
    Cela vous permettra d&#8217;enregistrer les changements (sudo permet de s&#8217;attribuer les droits de root). Regardez la fin du fichier qui ressemblera à :
  </p>
  
  <blockquote>
    <p>
      <em> kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro &#8230;<br /> </em>
    </p>
  </blockquote>
  
  <p>
    et rajouter l&#8217;option acpi=off :
  </p>
  
  <blockquote>
    <p>
      <em> kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 acpi=off ro &#8230;</em>
    </p>
  </blockquote>
  
  <p>
    Enregistrez les changements et redémarrez. Ca devrait être bon.
  </p>
  
  <p>
    Source d&#8217;aide principale : <a href="http://ubuntuforums.org/showthread.php?t=887797" target="_blank">http://ubuntuforums.org/showthread.php?t=887797</a>
  </p>
  
  <p>
    N&#8217;hésitez pas à poster des commentaires pour demander de l&#8217;aide.
  </p>