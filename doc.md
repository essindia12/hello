@startuml
!define RECTANGLE class

title Customer Master with Agentic AI - Architecture

actor "Sales Team / User" as User
actor "Finance Team" as Finance
actor "Compliance Team" as Compliance

RECTANGLE "Customer Data Input Layer" {
    User --> (Customer Onboarding Form)
}

RECTANGLE "Agentic AI Layer\n(Customer Master Intelligence Agent)" {
    (Data Validation Engine)
    (Duplicate Detection Engine)
    (Compliance Validator)
    (Credit Risk Scoring Engine)
    (Learning & Monitoring Engine)
}

RECTANGLE "Workflow & Governance Layer" {
    (Approval Workflow Engine)
    (Audit Trail & Explainability)
}

RECTANGLE "ERP Core (ebizframe.ai)" {
    (Customer Master Database)
    (Sales Module)
    (Finance Module)
    (CRM Module)
}

RECTANGLE "External Systems" {
    (GST / Tax APIs)
    (Credit Bureau / Financial Data)
}

' Flow
(Customer Onboarding Form) --> (Data Validation Engine)
(Data Validation Engine) --> (Duplicate Detection Engine)
(Duplicate Detection Engine) --> (Compliance Validator)
(Compliance Validator) --> (Credit Risk Scoring Engine)

(Credit Risk Scoring Engine) --> (Approval Workflow Engine)

(Approval Workflow Engine) --> (Customer Master Database)

(Customer Master Database) --> (Sales Module)
(Customer Master Database) --> (Finance Module)
(Customer Master Database) --> (CRM Module)

' External integrations
(Compliance Validator) --> (GST / Tax APIs)
(Credit Risk Scoring Engine) --> (Credit Bureau / Financial Data)

' Monitoring loop
(Customer Master Database) --> (Learning & Monitoring Engine)
(Learning & Monitoring Engine) --> (Credit Risk Scoring Engine)

@enduml
