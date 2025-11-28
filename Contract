// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BlockVerve {
    struct Event {
        string name;
        uint256 date; // Unix timestamp for event date
        uint256 attendeeCount;
    }

    mapping(uint256 => Event) public events;
    uint256 public eventCount;

    // Core function 1: Create a new event
    function createEvent(string memory _name, uint256 _date) public {
        require(bytes(_name).length > 0, "Event name cannot be empty");
        require(_date > block.timestamp, "Event date must be in the future");
        
        eventCount++;
        events[eventCount] = Event(_name, _date, 0);
    }

    // Core function 2: Register as an attendee for an event
    function registerAttendee(uint256 _eventId) public {
        require(_eventId > 0 && _eventId <= eventCount, "Invalid event ID");
        require(events[_eventId].date > block.timestamp, "Event has already passed");
        
        events[_eventId].attendeeCount++;
    }

    // Core function 3: Get details of an event
    function getEventDetails(uint256 _eventId) public view returns (string memory, uint256, uint256) {
        require(_eventId > 0 && _eventId <= eventCount, "Invalid event ID");
        
        Event memory e = events[_eventId];
        return (e.name, e.date, e.attendeeCount);
    }
}
