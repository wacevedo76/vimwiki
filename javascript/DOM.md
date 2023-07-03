--------------------------------------------------------------------------------
# JavaScript - Document Object Mode
--------------------------------------------------------------------------------
  **Node Object Types**          | A list of the most common types of nodes:
                             |   * DOCUMENT_NODE (e.g., window.document)
                             |   * ELEMENT_NODE (e.g., <body>, <a>, <p>, etc)
                             |   * ATTRIBUTE_NODE (e.g., class="funEdges")
                             |   * TEXT_NODE (e.g., text characters in an HTML
                             |        document including carriage returns and
                             |        whitespace)
                             |   * DOCUMENT_FRAGMENT_NODE (e.g., document.createDocumentFragment())
                             |   * DOCUMENT_TYPE_NODE (e.g., <!DOCTYPE html>)
                             |
  Node Interfaces/constructor| **Interface/constructor**                    **nodeType (returned from .nodeType)**
  and corresponding numeric  | HTML`*Element` [e.g., HTMLBodyElemen]       1 (i.e., ELEMENT_NODE)
  classification and name    | Text                                      3 (i.e., TEXT_NODE)
  given to instances         | Attr                                      2 (i.e., ATTRIBUTE_NODE)
                             | HTMLDocument                              9 (i.e., DOCUMENT_NODE)
                             | DocumentFragment                         11 (i.e., DOCUMENT_FRAGMENT_NODE)
                             | DocumentType                             10 (i.e., DOCUMENT_TYPE_NODE)
                             |
  Inheritance model for the  | * object < Node < Element <HTMLElement < (e.g., HTML`*Element`)
  most common node           | * object < Node < Attr (this is deprecated in DOM4)
  interfaces                 | * object < Node < CharacterData < Text
                             | * object < Node < Document < HTMLDocument
                             | * object < Node < DocumentFragment
                             |
                             | * Note: **Node** is just a JavaScript constructor
                             |         function (it inherits from Object.
                             |         prototype just like all objects in
                             |         JavaScript
                             |
  The most common Node prop- | *Node Properties*
  erties and methods inheri- |    * childNodes
  ted by all node objects    |    * firstChild
                             |    * lastChild
                             |    * next Sibling
                             |    * nodeName
                             |    * nodeType
                             |    * nodeValue
                             |    * parentNode
                             |    * preveiousSibling
                             |
                             | *Node Methods*
                             |    * appendChild()
                             |    * cloneNode()
                             |    * compareDocumentPosition()
                             |    * contains()
                             |    * hasChildNodes()
                             |    * insertBefore()
                             |    * isEqualNode()
                             |    * removeChild()
                             |    * replaceChild()
                             |
                             | *Document methods*
                             |    * document.createElement()
                             |    * document.createTextNode()
                             |
                             | *HTML`*Element` properties*
                             |    * innerHTML
                             |    * outerHTML
                             |    * textContent
                             |    * innerText
                             |    * outerText
                             |    * firstElementChild
                             |    * lastElementChild
                             |    * nextElementChild
                             |    * previousElementChild
                             |    * children
                             |
                             | *HTML element method*
                             |    * insertAdjacentHTML()
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
