---
title: Utiliser Latex avec Notepad++
author: Jice

date: 2009-09-08
url: /2009/09/utiliser-latex-avec-notepad/
categories:
  - Informatique
tags:
  - latex
  - Miktex
  - notepad++
---
### Introduction :

<p align="justify">
  Pour la plupart des développements que j&#8217;effectue (php, C, python&#8230;) je tire partie des fonctionnalités de l&#8217;éditeur Notepad++ sous Windows. Dans l&#8217;article qui suit, je vous présente une installation clé en main pour utiliser LateX de manière agréable grâce à Notepad++.
</p>

<p align="justify">
  <h3>
    Installation de MikTex :
  </h3>
  
  <p align="justify">
    Afin d&#8217;être &#8216;compiler&#8217;, un document Latex doit utiliser un certain nombre de librairies. Sous windows, le logiciel qui vous permet de compiler votre code LateX s&#8217;appelle <a href="http://miktex.org/" target="_blank">MikTex</a>. Vous pouvez télécharger la version à partir de laquelle est basé ce tutorial à l&#8217;adresse : <a href="http://miktex.org/2.7/Setup.aspx" target="_blank">http://miktex.org/2.7/Setup.aspx</a>
  </p>
  
  <p align="justify">
    Installer la version basique. Il n&#8217;y a pas d&#8217;option spéciale à choisir, vous pouvez cliquer sur &#8216;next&#8217; à cuaque écran.
  </p>
  
  <p align="justify">
    <h3>
      Installation de Notepad++ :
    </h3>
    
    <p align="justify">
      L&#8217;éditeur de texte <a href="http://notepad-plus.sourceforge.net/fr/site.htm" target="_blank">Notepad++</a> est l&#8217;un des plus pratiques que j&#8217;ai pu utiliser sous windows. Coloration syntaxique, numérotation des lignes, recherche/remplacement aisé. Il est très rapide à prendre en main.
    </p>
    
    <p align="justify">
      Vous pouvez télécharger la dernière version de notepad++ sur <a href="http://sourceforge.net/project/showfiles.php?group_id=95717&package_id=102072">sa Forge</a>.
    </p>
    
    <p align="justify">
      <h3>
        Configurer Notepad++ pour marcher avec PDFLateX :
      </h3>
      
      <p align="justify">
        Je ne présenterai la manipulation à réaliser que pour PDFLatex. Si vous voulez l&#8217;adapter à Latex, il n&#8217;y aura pas beaucoup de modification (retirer &#8216;pdf&#8217; dans le mot &#8216;pdflatex&#8217; &#8230;. pas trop dur?).
      </p>
      
      <p align="justify">
        Ouvre le logiciel Notepad++, et cliquer sur le menu &#8216;Exécution&#8217; (&#8216;Run&#8217; dans la version anglaise) puis sur &#8216;Executer&#8217;. Rentrer à présent l&#8217;instruction suivante dans le champ de texte :
      </p>
      
      <blockquote>
        <p align="justify">
          <em>pdflatex.exe -src-specials &#8220;$(FULL_CURRENT_PATH)&#8221;</em>
        </p>
      </blockquote>
      
      <p align="justify">
        Pour enregistrer cette commande de manière définitive dans Notepad++, cliquez sur &#8216;Sauver&#8217; et assigner lui un nom et un raccourci.
      </p>
      
      <p align="justify">
        Vous pouvez ensuite rajouter la commande suivante, qui vous permet de visualiser votre fichier avec Acrobat Reader si vous l&#8217;avez. Toujours dans &#8216;Executer&#8217; rentrez :
      </p>
      
      <blockquote>
        <p align="justify">
          <em>acrord32 &#8220;$(CURRENT_DIRECTORY)\$(NAME_PART).pdf&#8221;</em>
        </p>
        
        <p align="justify">
          </blockquote> 
          
          <h3>
            Changer les raccourcis de Notepad++ :
          </h3>
          
          <p align="justify">
            Après un certain temps vous pourriez être amenés à vouloir changer les raccourcis de Notepad++, ou à vouloir les effacer. Pour cela, rendez-vous dans le répertoire :
          </p>
          
          <blockquote>
            <p align="justify">
              C:\Documents and Settings\<span style="color: #ff0000;">votre_nom_d_utilisateur</span>\Application Data\Notepad++
            </p>
          </blockquote>
          
          <p align="justify">
            Et modifiez le document <strong>shortcuts.xml</strong>. Vous devriez arriver à retrouver les lignes utiles.
          </p>
          
          <p align="justify">
            <h3>
              Configuration Avancée pour Windows XP :
            </h3>
            
            <p align="justify">
              Lorsque vous voudrez profiter pleinement de LateX, vous voudrez utiliser des extensions qui ne sont compatibles qu&#8217;avec une compilation ps (par exemple PSTricks pour faire des schémas). Ainsi donc, vous serez obligés de lancer une compilation en LateX vers .dvi (la compilation normale), puis de convertir en .ps puis en .pdf. Pour cela, MikteX contient déjà les outils qu&#8217;il faut. Ils sont rangés avec latex.exe et pdflatex.exe dans le répertoire d&#8217;installation (pour infos, chez moi c&#8217;est à : C:\Program Files\MiKTeX 2.7\miktex\bin). Il faudra donc utiliser ps2pdf.exe (pour passer d&#8217;un .ps à un .pdf), ou dvipdfm.exe (pour passer plus rapidement d&#8217;un dvi à un pdf).
            </p>
            
            <p align="justify">
              <p align="justify">
                J&#8217;ai donc créer un fichier batch pour automatiser la chose. Je l&#8217;ai nommé <strong>notepad.bat</strong>, et je l&#8217;ai placé dans le répertoire des binaires de MikTex.
              </p>
              
              <p align="justify">
                Voilà le batch en question :
              </p>
              
              <blockquote>
                <p align="justify">
                  <em>echo %1<br /> latex -src-specials %1<br /> cd %2<br /> dvipdfm %3.dvi<br /> rm %3.dvi</em>
                </p>
              </blockquote>
              
              <p align="justify">
                De retour dans Notepad,enregistrez la commande :
              </p>
              
              <blockquote>
                <p align="justify">
                  <em>notepad.bat &#8220;$(FULL_CURRENT_PATH)&#8221; &#8220;$(CURRENT_DIRECTORY)&#8221; &#8220;$(NAME_PART)&#8221;</em>
                </p>
              </blockquote>
              
              <p align="justify">
                Dans le .bat, le %1, %2 et %3 correspondent aux arguments envoyer au script. Dans la commande de notepad, je lui envoie donc à la suite les 3 arguments.
              </p>
              
              <p align="justify">
                <p align="center">
                  <a href="http://jice.lavocat.name/fr/download/category/8-informatique?download=21%3Abatch-compilation-latex-avec-notepad" target="_blank">Téléchargement du fichier batch</a> encore plus évolué (prend en compte la génération d&#8217;une bibliographie).
                </p>
                
                <p align="center">
                  <p align="justify">
                    N&#8217;hésitez pas à poser vos questions en commentaire si ce n&#8217;est pas clair. N&#8217;hésitez pas non plus à lire le fichier batch qui contient des commentaires.
                  </p>
                  
                  <p align="justify">
                    <h2>
                      Configuration pour Windows Vista
                    </h2>
                    
                    <p>
                      Sous windows vista, la gestion des droits des utilisateurs empêche un déroulement classique de la compilation. Tous les fichiers intérmédiaires sont stockés dans le répertoire où se trouvent les binaires (pagaille en perspective). Néanmoins, en rajoutant des options à votre fichier batch il est possible de controller :
                    </p>
                    
                    <ol>
                      <li>
                        l&#8217;emplacement où chercher les fichier sources (images, bibliographie, etc)
                      </li>
                      <li>
                        l&#8217;emplacement des fichier de sorties
                      </li>
                    </ol>
                    
                    <p>
                      Grâce au fichier batch suivant il vous est possible de contrôller plus en détail la façon dont se passe votre compilation
                    </p>
                    
                    <p style="text-align: center;">
                      <a href="http://jice.lavocat.name/fr/download/category/8-informatique?download=22%3Abatch-compilation-latex-avec-notepad-windows-vista" target="_blank">Téléchargement du fichier batch</a> pour Vista
                    </p>
                    
                    <p style="text-align: justify;">
                      N&#8217;hésitez pas à poser vos questions en commentaire si ce n&#8217;est pas clair. N&#8217;hésitez pas non plus à lire le fichier batch qui contient des  commentaires (A associer avec le batch pour XP pour comprendre un peu plus leur fonctionnement)
                    </p>