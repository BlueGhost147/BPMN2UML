## BPMN2UML

The BPMN standard is based on the principles of the Meta Object Facility (MOF) and therefore defines the semantics of the modeling language as a metamodel using UML classes. This means that each process model must be traceable to a class hierarchy.

### Content and goals

The goal of the project is to analyze the BPMN standard and to create a preferably complete UML diagram (class diagram). The UML diagram is based on the [BPMN standard 2.0.2](https://www.omg.org/spec/BPMN/2.0.2/)

### Requirements

Required Software:

* [Visual Paradigm](https://www.visual-paradigm.com/download/community.jsp)

### Setup
* Download or clone the repository
* Open ./VisualParadigm_Project/BPMN2UML_V2.vpp with Visual Paradigm
* In the Diagram Navigator > BPMN2UML > Class Diagram > Open BPMN2UML


### BPMN standard as a UML class diagram

![BPMN2UML class diagram](./ClassDiagram/BPMN2UML_classDiagram.jpg "class diagram")

#### Conformance classes

The conformance classes of BPMN are marked by different background colors (classes and attributes).

**The conformance classes of BPMN:**

* Descriptive conformance sub-class (cyan)
* Analytic conformance sub-class (green)
* Common executable conformance sub-class (orange)
* Process modelling conformance class (white)
* For process execution (yellow)

### Proof of concept - A BPMN model as a object diagram

As proof of concept, an object diagram was created with the created class diagram, which represents an exemplary BPMN model.

#### Exemplary BPMN model

The following BPMN model was used for the proof of concept.
![Test BPMN](./ObjectDiagram/BPMN2UML_Test_BPMN.jpg "Test BPMN")

#### BPMN model as XML (simplified)

Simplified XML structure of the BPMN model:

<details>

````xml
<?xml>
   <process id="sid-21543069-f5db-4c09-8a35-c13bb8558a3e" isClosed="false" isExecutable="false" processType="None">
      <startEvent id="sid-C6FC241F-F72E-4720-BE76-FDD590A42CB6" name="Start1">
         <outgoing>sid-62B4BF65-7D17-4656-88AF-D0AC23817F7D</outgoing>
      </startEvent>
      <task completionQuantity="1" id="sid-1678751B-3DFD-4C2F-B0B1-2BC82502AD5E" isForCompensation="false" name="Task1" startQuantity="1">
         <incoming>sid-62B4BF65-7D17-4656-88AF-D0AC23817F7D</incoming>
         <outgoing>sid-9BEB1D13-5E3F-485A-A8D7-4FB975A6C647</outgoing>
      </task>
      <endEvent id="sid-8713CB15-5127-407C-8B73-D2A7487CB9D6" name="End1">
         <incoming>sid-D2A826FE-6253-47FD-9B2C-A243044A034C</incoming>
         <incoming>sid-CB58CE8F-707A-4498-BB42-ADDA41420911</incoming>
      </endEvent>
      <exclusiveGateway gatewayDirection="Diverging" id="sid-0E620CE2-39F3-4DC3-B2BA-B4C0EF663099" name="Successful?">
         <incoming>sid-9BEB1D13-5E3F-485A-A8D7-4FB975A6C647</incoming>
         <outgoing>sid-91E8499A-E839-4D5C-B7B8-53BA0886EDED</outgoing>
         <outgoing>sid-7CB37B08-D365-4F97-82DC-B6BB0DBD5F2D</outgoing>
      </exclusiveGateway>
      <task completionQuantity="1" id="sid-AAA09D7E-AFF9-475A-9388-388D560295E6" isForCompensation="false" name="Task2 - A" startQuantity="1">
         <incoming>sid-7CB37B08-D365-4F97-82DC-B6BB0DBD5F2D</incoming>
         <outgoing>sid-D2A826FE-6253-47FD-9B2C-A243044A034C</outgoing>
      </task>
      <task completionQuantity="1" id="sid-81900967-2F94-4816-8762-C15280E4F745" isForCompensation="false" name="Task2 - B" startQuantity="1">
         <incoming>sid-91E8499A-E839-4D5C-B7B8-53BA0886EDED</incoming>
         <outgoing>sid-CB58CE8F-707A-4498-BB42-ADDA41420911</outgoing>
      </task>
      <sequenceFlow id="sid-62B4BF65-7D17-4656-88AF-D0AC23817F7D" name="" sourceRef="sid-C6FC241F-F72E-4720-BE76-FDD590A42CB6" targetRef="sid-1678751B-3DFD-4C2F-B0B1-2BC82502AD5E">
      </sequenceFlow>
      <sequenceFlow id="sid-9BEB1D13-5E3F-485A-A8D7-4FB975A6C647" name="" sourceRef="sid-1678751B-3DFD-4C2F-B0B1-2BC82502AD5E" targetRef="sid-0E620CE2-39F3-4DC3-B2BA-B4C0EF663099">
      </sequenceFlow>
      <sequenceFlow id="sid-91E8499A-E839-4D5C-B7B8-53BA0886EDED" name="no" sourceRef="sid-0E620CE2-39F3-4DC3-B2BA-B4C0EF663099" targetRef="sid-81900967-2F94-4816-8762-C15280E4F745">
      </sequenceFlow>
      <sequenceFlow id="sid-7CB37B08-D365-4F97-82DC-B6BB0DBD5F2D" name="yes" sourceRef="sid-0E620CE2-39F3-4DC3-B2BA-B4C0EF663099" targetRef="sid-AAA09D7E-AFF9-475A-9388-388D560295E6">
      </sequenceFlow>
      <sequenceFlow id="sid-D2A826FE-6253-47FD-9B2C-A243044A034C" name="" sourceRef="sid-AAA09D7E-AFF9-475A-9388-388D560295E6" targetRef="sid-8713CB15-5127-407C-8B73-D2A7487CB9D6">
      </sequenceFlow>
      <sequenceFlow id="sid-CB58CE8F-707A-4498-BB42-ADDA41420911" name="" sourceRef="sid-81900967-2F94-4816-8762-C15280E4F745" targetRef="sid-8713CB15-5127-407C-8B73-D2A7487CB9D6">
      </sequenceFlow>
   </process>
   <bpmndi:BPMNDiagram id="sid-140bc4a4-1889-4f59-b8c1-2043e114ba49">
      <!-- Diagram and rendering information -->
   </bpmndi:BPMNDiagram>
</definitions>

````


</details>

#### Object diagram of the BPMN model

The following UML object diagram can be derived from the XML code:

![Object diagram](./ObjectDiagram/Obj_BPMN2UML_Test1.jpg "Object diagram")
