# Strobe-enhanced microscopy stage for microfluidic droplet generation [![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)

The strobe-enhanced microscopy stage is a free and open-source workstation for imaging fast processes, particularly developed for microfluidic droplet generation. It uses the lens from the Raspberry Pi Camera to produce a microscope with a field of view of almost 1mm and a strobe illumination based on a high-power LED for imaging fast-moving objects. Custom electronics allow the synchronization between the LED and the camera to capture sharp images of fast-moving droplets and other objects.

> **Note:** Most parts of this stage are original designs, and some items were modified from the open-source hardware [OpenFlexure flat-top microscope](https://rwb27.gitlab.io/openflexure-flat-top-microscope/), this includes some elements on this page and in the assembly instructions.

Find about more about this platform and other open-source hardware for bioimaging on the [LIBRE hub website](https://librehub.github.io/). Follow us! [#twitter](https://twitter.com/WenzelLab) [#YouTube](https://www.youtube.com/@librehub) [#LinkedIn](https://www.linkedin.com/company/92802424) [#instagram](https://www.instagram.com/wenzellab/) [#Printables](https://www.printables.com/@WenzelLab), [IIBM website](https://ingenieriabiologicaymedica.uc.cl/en/people/faculty/821-tobias-wenzel)

<!--- ## Table of Contents --->

<!--- ## Background --->

## Usage

### Instructions

* [Assembly instructions](https://wenzel-lab.github.io/strobe-enhanced-microscopy-stage/)
    * [Parts list](https://wenzel-lab.github.io/strobe-enhanced-microscopy-stage/3-level-station_BOM.html)
    * [Software installation](https://wenzel-lab.github.io/strobe-enhanced-microscopy-stage/software-installation.html)
* Usage instructions
	* [Software usage](https://wenzel-lab.github.io/strobe-enhanced-microscopy-stage/usage.html)

This project is documented with GitBuilding - an OpenSource project for documenting hardware projects. For more information on the GitBuilding project, or how
to install GitBuilding please see the [GitBuilding website](http://gitbuilding.io)

## Design files and source code

* Hardware designs
    * [Microscope hardware and assembly instructions (source)](https://github.com/wenzel-lab/strobe-enhanced-microscopy-stage)
    * [Pi Hat](https://github.com/wenzel-lab/moldular-microfluidics-workstation-controller/tree/master/module-pi/pi_pcb)
    * [Strobe module](https://github.com/wenzel-lab/moldular-microfluidics-workstation-controller/tree/master/module-fast-imaging)
* Software source code
    * [Microscope server](https://github.com/wenzel-lab/moldular-microfluidics-workstation-controller/blob/master/module-pi/webapp.zip) (This code runs on the built-in Raspberry Pi and includes the web application for the user interface.)
    * Microscope operating system (This collates all software and builds a pre-written SD card image for the Raspberry Pi.) - Coming soon
 
### How do I edit the documentation?

To edit the documentation you do not need to install anything, but you will need to
install something to build the final version of the documentation (such as a website).
The documentation files can be opened in a plain text editor such as Windows Notepad,
Notepad++, gedit, VS Code, etc. GitBuilding also comes with a browser-based editor that
displays has a live display of the final HTML documentation.

If you have ever used [markdown](https://www.markdownguide.org/basic-syntax/) you will
notice that the files you are editing are markdown files. GitBuilding uses an extended
markdown syntax (that we call BuildUp). This allows you to keep track of parts in the
documentation. More detail on the documentation is available on the
[GitBuilding website](https://gitbuilding.io/syntax/). There is also additional
[syntax for configuration](https://gitbuilding.io/syntax/buildconfsyntax), and for
[part libraries](https://gitbuilding.io/syntax/builduplibrary/).

## Contribute

You're free to fork the project and enhance it. If you have any suggestions to improve it or add any additional functions make a pull-request or [open an issue](https://github.com/wenzel-lab/strobe-enhanced-microscopy-stage/issues/new).
For interactions in our team and with the community applies the [GOSH Code of Conduct](https://openhardware.science/gosh-2017/gosh-code-of-conduct/).

## License

[CERN OHL 2W](LICENSE) © Tobias Wenzel, Matías Hurtado, and Pierre Padilla-Huamantinco. This project is Open Source Hardware - please acknowledge us when using the hardware or sharing modifications.
