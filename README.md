# Compilerdesign
Das erste Design des Compilerbauprojektes, was Teil der Prüfungsleistung des Fachs Compilerbau an der Hochschule Bochum ist.

Dieser Compiler nimmt mathematische Ausdrücke in Form römische Zahlen und Operatoren (+,-,*,/,%), konvertiert die römischen Zahlen in arabischen Zahlen nach den offiziellen Umwandlungsregeln, scannt und parst die Eingabe (prüft die Eingabe auf syntaktische sowie semantische korrektheit), erzeugt den abstrakten Syntaxbaum nach definierter Sprachgrammatik, erzeugt den ZwischenCode in der PostFix-Notation (in Form Operand, Operand, Operator) und berechnet ebenfalls im Endeffekt das Ergebnis des Ausdrücks nach den mathematischen Berechnungsregeln.

Der Compiler hat 5 Kernbestandteile nämlich Lexer, Converter, Parser, ZwischenCodeErzeuger und der Kellermaschine.

1. Lexer: Der Lexer scannt die Eingabe (in Form römische Zahlen und Operatoren), entfernt Leerzeichen in der Eingabe, prüft nach lexikalischer Korrektheit und weist allen Eingabezeichen jeweiligen Tokens hinzu.

2. Converter: Der Converter wandelt die Eingabezeichen (insbesondere der römischen Zahlen in der Eingabe) zu der Form arabischen Zahlen nach den offiziellen Regeln zum Umwandeln römischer in arabischer Zahlen, prüft nach semantischer Korrektheit und weist wieder die neue Array Tokens hinzu.

3. Parser: Der Parser prüft die Ausgabe vom Converter nach syntaktischer Korrektheit über die definierte Sprachgrammatik und erzeugt den abstrakten Syntaxbaum mithilfe des NodePrinters.

4. ZwischenCodeErzeuger: Der ZwischenCodeErzeuger nimmt die Ausgabe vom NodePrinter bzw. Parser und erzeugt den ZwischenCode in der PostFix-Notation (Operand, Operand, Operator), damit der Code auf mehrere Kellermaschinen portiert werden kann.

5. Kellermaschine: In diesem Compiler wurde die Kellermaschine über die Node-Klasse hinaus realisiert. Die Methode evaluate() wurde von ValueNode, UnaryNode sowie BinaryNode vererbt und wird zum Berechnen des mathematischen Ergebnis in dem Parser genutzt.

Sonstige Teile des Compilers
1. Type und Token: Die Klassen Type und Token werden überall in dem FrontEnd des Compilers nämlich Lexer, Converter und Parser verwendet, um den Eingabezeichen Tokens zuzuweisen.

2. NodePrinter: Nimmt die Eingabe vom Parser (in Form linker Teil, Operator, rechter Teil) und erzeugt den abstrakten Syntaxbaum nach definierter Sprachgrammatik (über die Methoden expression(), term(), und factor() des Parsers).

3. Node: Node ist eine abstrakte Klasse, die die Methoden evaluate() und toString() beinhält, die von anderen Klassen, die Node vererben, überschrieben bzw. overridet.

4. ValueNode:
   toString(): gibt einfach den String-Wert des Eingabezeichens zurück
   evaluate(): gibt den umgewandelten Double()-Wert des Eingabezeichens zurück

5. UnaryNode:
   toString(): Stellt die Eingabezeichen in Form: "UnaryNode{operator= operatorValue, right= rightValue}" auf Basis des bevorstehenden Operators dar.
   evaluate(): gibt entweder den positiven- oder den negativen-Wert des Eingabezeichens auf Basis des bevorstehenden Operators zurück.

6. BinaryNode:
   toString(): Stellt die Eingabezeichen in Form: "{left= leftValue, operator= operatorValue, right= rightValue}" auf Basis des bevorstehenden Operators dar.
   evaluate(): Wendet die jeweilige mathemtische Operation auf den linken und den rechten Eingabeteil des Parser an und gibt das berechnete Erdergebnis zurück.
