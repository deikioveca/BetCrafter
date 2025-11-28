BetCrafter
-
BetCrafter is a backend system for managing and analyzing football betting tickets. It provides APIs for ticket storage, updates, and insights generation — helping user track performance and identify patterns to improve betting strategies over time.


Features
-
* Ticket management
  * Create new football betting tickets
  * Retrieve pending tickets
  * Update pending tickets
  * Get ticket by status or id
* Data analysis
  * Analyze ticket history and performance
  * Provide insights and trends to improve future betting decisions
* User interaction
  * Supports both cli and web interfaces
  * Easy-to-use endpoints for ticket management and data analysis
* Database integration
  * Store tickets and analysis data in PostgreSQL
  * Maintain historical records for trend analysis


Technologies used
-
* Go
* GORM
* PostgreSQL
* Docker


Running guide
-
* Prerequisites
  * Go installed
  * Docker installed
  * PostgreSQL installed
* Locally
  * Clone the repo
  * Run go mod download
  * Start PostgreSQL and ensure that database betcrafter exist
  * Create and config .env file according to your setup
  * go run cmd/cli/main.go -> for the cli && go run cmd/web/main.go -> for the web
* Docker
  * Docker compose up


Workflow
-
* Create ticket              - store a new football betting ticket with stake and matches info
* Get pending ticket         - retrieve all tickets that are not yet resolved
* Update pending ticket      - modify ticket info: profit, cashout(true,false), status(won,lost), match result outcome if it's correct or wrong
* Get ticket by status or id - retrieve tickets by status or ticket by id
* Analyze tickets            - retrieve useful information about the tickets from date range: for example the 3 most profitable outcomes, overall statistic, etc.

API Endpoints
-
| Method     | Endpoint                                                  | Description                                                                        |
| -----------| ----------------------------------------------------------| -----------------------------------------------------------------------------------|
| **POST**   | `/ticket/create`                                          | Create ticket                                                                      |
| **GET**    | `/ticket/getPending`                                      | Get pending tickets                                                                |
| **PATCH**  | `/ticket/updatePending`                                   | Update pending ticket                                                              |
| **PATCH**  | `/ticket/updateDate`                                      | Update ticket date                                                                 |
| **GET**    | `/ticket/getById/{ticketID}`                              | Get ticket by id                                                                   |
| **GET**    | `/ticket/getByStatus/{status}`                            | Get ticket by status                                                               |
| **GET**    | `/ticket/getStats`                                        | Get ticket stats in given date range                                               |
| **GET**    | `/ticket/getPickedOutcomeStats`                           | Get ticket picked outcome stats in given date range                                |
| **GET**    | `/ticket/getPickedOutcomeOddRangeStats`                   | Get ticket picked outcome odd range stats  in given date range                     |
| **GET**    | `/ticket/getMostProfitablePick`                           | Get most profitable pick outcomes in given date range                              |
